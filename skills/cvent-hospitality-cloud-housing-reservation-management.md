---
name: cvent-housing-reservation-management
description: >-
  Manage Cvent Passkey housing reservations directly — check availability and inventory, create,
  modify and cancel a reservation, and unwind a booking correctly.
api: cvent-hospitality-cloud:housing
generated: '2026-09-07'
method: generated
source: openapi/cvent-hospitality-cloud-housing-openapi.yml
operations:
  - getHousingEventHotelAvailability
  - getRoomTypeDetails
  - getRoomTypeInventory
  - getHousingEventInventory
  - createReservation
  - getReservation
  - updateReservationSync
  - cancelReservation
  - cancelReservationRequest
  - unlinkReservation
  - getHousingEventReservations
base_url: https://api-platform.cvent.com/ea
scopes:
  - housing/housing-event-available-nights:read
  - housing/housing-event-inventory:read
  - housing/housing-event-room-types:read
  - housing/reservations:read
  - housing/reservations:write
  - housing/reservations:delete
  - housing/reservation-requests:delete
  - housing/reservations-link:delete
---

# Manage a Passkey housing reservation end to end

Use this when your application owns the whole booking, rather than handing the guest a link. Cvent's
own guidance is that this flow takes longer to build and needs more testing than the bridge flow.

## Availability first

- `getHousingEventHotelAvailability` —
  `GET /housing-events/{housingEventId}/hotels/{hotelId}/available-nights`
- `getRoomTypeDetails` —
  `GET /housing-events/{housingEventId}/hotels/{hotelId}/room-types/{roomTypeId}`
- `getRoomTypeInventory` —
  `GET /housing-events/{housingEventId}/hotels/{hotelId}/room-types/{roomTypeId}/inventory`
- `getHousingEventInventory` — `GET /housing-events/{housingEventId}/inventory` for the whole block

## Book, modify, read

- `createReservation` — `POST /reservations`
- `getReservation` — `GET /reservations/{reservationId}`
- `updateReservationSync` — `PUT /reservations/{reservationId}`
- `getHousingEventReservations` — `GET /housing-events/{housingEventId}/reservations`

## Undoing things — read this before you cancel anything

There are two objects and they cancel independently. Getting this wrong leaves a guest holding a room
they think they released, or releases a room they think they still have.

| You want to | Call | What it does NOT do |
|---|---|---|
| Release the hotel booking | `cancelReservation` — `DELETE /reservations/{reservationId}` | Does **not** cancel the reservation request |
| Withdraw the bridge | `cancelReservationRequest` — `DELETE /reservation-requests/{reservationRequestsId}` | Does **not** cancel a reservation already booked through it |
| Detach a booking from a request | `unlinkReservation` — `DELETE /reservation-requests/{reservationRequestsId}/reservations/{reservationId}` | Does **not** cancel or change the reservation itself |

Sequences that work:

- **Guest cancels the room, keeps their spot:** `cancelReservation`, then `unlinkReservation` so a new
  reservation can be linked to the same request.
- **Guest drops out entirely:** `cancelReservation`, `unlinkReservation`, then
  `cancelReservationRequest`. You cannot cancel a request while a reservation is still linked to it.

**No published cancellation window.** Cvent documents the preconditions for every reversal but states
no deadline by which a cancellation is accepted. Do not assume one; check the hotel's own terms on the
room type.

## Runtime rules

Same as the rest of this contract: OAuth 2.0 bearer, 60-minute tokens, cursor pagination on
`paging.currentToken`, errors as `{code, message, details[]}` in `application/json` (not RFC 9457),
`X-RateLimit-*` headers, 429 with no `Retry-After`, and no idempotency key anywhere — so a retried
`POST /reservations` can double-book.
