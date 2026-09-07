---
name: cvent-venue-profile-maintenance
description: >-
  Keep a venue's profile, facility details and meeting-room inventory current in the Cvent Supplier
  Network from a property management or CMS system.
api: cvent-hospitality-cloud:venue-profiles
generated: '2026-09-07'
method: generated
source: >-
  openapi/cvent-hospitality-cloud-venue-profiles-openapi.yml,
  openapi/cvent-hospitality-cloud-venue-meeting-rooms-openapi.yml
operations:
  - getVenueDetailsOverview
  - updateVenueDetails
  - patchVenueDetails
  - updateVenueFacility
  - patchVenueFacility
  - createMeetingRoom
  - listMeetingRoomsOverviews
  - getMeetingRoomOverview
  - updateMeetingRoom
  - patchMeetingRoom
  - associateMeetingRoomImage
  - listMeetingRoomImages
  - disassociateMeetingRoomImage
base_url: https://api-platform.cvent.com/ea
scopes:
  - venue/venue-details-overview:read
  - venue/venue-details:write
  - venue/venue-facility:write
  - venue/meeting-rooms:write
  - venue/meeting-room-overviews:read
  - venue/meeting-room-images:read
  - venue/meeting-room-images:write
  - venue/meeting-room-images:delete
---

# Keep a venue profile current

Cvent shipped this surface in July 2026 (Venue Profiles and Venue Meeting Rooms both appear as new tags
in the 22-23 July release), with meeting-room images following on 19-20 August. It is new, so expect it
to keep moving; check the changelog before a release.

## Read the current state first

- `getVenueDetailsOverview` — `GET /venues/{venueId}/details/overview`
- `listMeetingRoomsOverviews` — `GET /venues/{venueId}/meeting-rooms/overviews`
- `getMeetingRoomOverview` — `GET /venues/{venueId}/meeting-rooms/{meetingRoomId}/overview`

## Update — and prefer PATCH

Every writable resource here offers both a PUT and a PATCH:

| Resource | Replace | Merge |
|---|---|---|
| Venue details | `updateVenueDetails` `PUT /venues/{venueId}/details` | `patchVenueDetails` `PATCH /venues/{venueId}/details` |
| Venue facility | `updateVenueFacility` `PUT /venues/{venueId}/facility` | `patchVenueFacility` `PATCH /venues/{venueId}/facility` |
| Meeting room | `updateMeetingRoom` `PUT /venues/{venueId}/meeting-rooms/{meetingRoomId}` | `patchMeetingRoom` `PATCH .../{meetingRoomId}` |

Use PATCH unless you genuinely hold the whole resource. A PUT is a full replace and there is no version
history, no restore and no undo on this surface — reversing a bad PUT means re-sending the previous
document, which only works if you kept it. Snapshot the overview before you write.

## Meeting rooms

- Create: `createMeetingRoom` — `POST /venues/{venueId}/meeting-rooms`. **There is no delete
  operation for a meeting room.** Creation is, on the public contract, irreversible — get it right, or
  you are left updating a room you did not want.
- Images: `associateMeetingRoomImage` — `PUT /venues/{venueId}/meeting-rooms/{meetingRoomId}/images`,
  `listMeetingRoomImages` — `GET .../images`, `disassociateMeetingRoomImage` —
  `DELETE .../images/{imageId}`. Images are the one thing here you can cleanly take back.

## Runtime rules

OAuth 2.0 bearer with 60-minute tokens; `X-RateLimit-*` headers, 429 with no `Retry-After`; errors as
`{code, message, details[]}`. No idempotency key — a retried `POST /venues/{venueId}/meeting-rooms`
creates a duplicate room you cannot delete.
