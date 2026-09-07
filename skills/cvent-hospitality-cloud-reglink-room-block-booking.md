---
name: cvent-reglink-room-block-booking
description: >-
  Send a registrant to Cvent Passkey to book a hotel room out of an event room block (the RegLink
  "bridge" flow) and reconcile the booking back into your system when the callback fires.
api: cvent-hospitality-cloud:housing
generated: '2026-09-07'
method: generated
source: >-
  openapi/cvent-hospitality-cloud-housing-openapi.yml,
  https://developers.cvent.com/docs/passkey/REST/getting-started,
  https://developers.cvent.com/docs/passkey/REST/callbacks
operations:
  - createConnection
  - getHousingEventsSummaries
  - getHousingEventInfo
  - getHousingEventHotels
  - getHousingEventRoomTypes
  - createReservationRequest
  - getReservationRequest
  - linkReservation
base_url: https://api-platform.cvent.com/ea
scopes:
  - housing/connections:write
  - housing/housing-events:read
  - housing/housing-event-hotels:read
  - housing/housing-event-room-types:read
  - housing/reservation-requests:write
  - housing/reservation-requests:read
  - housing/reservations-link:write
---

# Book a room block reservation through Passkey RegLink

This is the flow Cvent recommends when the guest should do the booking themselves. You pre-populate
their details, hand them a unique link, and Passkey tells you what happened.

## Before you start

- Passkey is an add-on licence. Credentials come from the Cvent Passkey RegLink API team, not from
  self-serve signup.
- The event owner must authorize your integration on each event before it works in production.
- Get a token: `POST /oauth2/token` (`oauth2Token`) with HTTP Basic `client_id:client_secret`.
  Tokens last 60 minutes. Ask for only the scopes above — a token with ~50+ scopes returns HTTP 431.

## Steps

1. **Establish the connection.** `createConnection` — `POST /connections`. This is the one-time link
   between your system and the Passkey event.
2. **Find the housing event.** `getHousingEventsSummaries` — `GET /housing-events/summaries`, then
   `getHousingEventInfo` — `GET /housing-events/{housingEventId}` for the detail. Read
   `reservationAccessDate` and `hotelCloseDate` from the hotel record before you send anyone anywhere;
   outside that window the booking will not be accepted and there is no test clock to move past it.
3. **List what is bookable.** `getHousingEventHotels` — `GET /housing-events/{housingEventId}/hotels`,
   then `getHousingEventRoomTypes` —
   `GET /housing-events/{housingEventId}/hotels/{hotelId}/room-types`.
4. **Create the bridge.** `createReservationRequest` — `POST /reservation-requests`. Set your own
   `sourceId`: it is the only correlation key you get back on the callback, and there is no
   idempotency key on this API, so a retried POST can create a second request. Record the returned
   reservation request id before you retry anything.
5. **Let the guest book.** They use Passkey's booking site, or staff book through the Call Center form.
6. **Receive the callback.** Passkey POSTs form-encoded data to your URL with `[[eventId]]`,
   `[[sourceId]]`, `[[reservationRequestId]]`, `[[reservationId]]`, `[[status]]` and
   `[[hotelConfNumber]]`. **Return HTTP 200.** Anything else is discarded — there is no retry and no
   dead letter queue. `[[status]]`: 0 New, 1 Cancelled, 2 Modified, 3 Modified and Cancelled,
   5/7 No Show, 8 Waitlist/Pending.
7. **Reconcile.** `getReservationRequest` — `GET /reservation-requests/{reservationRequestsId}`. If you
   booked the room yourself rather than through the link, attach it with `linkReservation` —
   `POST /reservation-requests/{reservationRequestsId}/reservations/{reservationId}`.

## Rules that will bite you

- **No idempotency.** Nothing in this contract accepts an idempotency key. Dedupe on your own
  `sourceId` before re-POSTing.
- **Cancelling is two separate actions.** Cancelling the request does not cancel a linked booking, and
  cancelling the booking does not cancel the request. See the housing-reservation-management skill.
- **You cannot cancel a request that has a linked reservation** — `unlinkReservation` first.
- **Rate limits.** `X-RateLimit-Limit` / `-Remaining` / `-Reset` on every response; 429 on exhaustion
  and **no `Retry-After`**. Back off 2s + 1-1000ms jitter, doubling to 16s, five attempts maximum. A
  daily-quota 429 will not clear until after midnight UTC, and every request — including the 429 —
  counts against quota.
- **Pick your region.** `https://api-platform.cvent.com/ea` or `https://api-platform-eur.cvent.com/ea`.
  Accounts do not span the two.
