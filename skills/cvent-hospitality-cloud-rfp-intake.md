---
name: cvent-rfp-intake
description: >-
  Pull a Cvent Supplier Network RFP and everything attached to it — agenda, guest rooms, questions,
  attachments, suppliers and recipient history — into a downstream sourcing or CRM system.
api: cvent-hospitality-cloud:rfp-management
generated: '2026-09-07'
method: generated
source: >-
  openapi/cvent-hospitality-cloud-rfp-management-openapi.yml,
  openapi/cvent-hospitality-cloud-rfp-requirements-openapi.yml,
  openapi/cvent-hospitality-cloud-rfp-suppliers-openapi.yml,
  openapi/cvent-hospitality-cloud-rfp-additional-details-openapi.yml,
  openapi/cvent-hospitality-cloud-proposal-drafts-openapi.yml
operations:
  - getRFP
  - listRfpAgendaItems
  - listRfpAgendaItemSchedules
  - getRfpGuestRooms
  - listRfpQuestions
  - listRfpCustomFields
  - listRfpAttachments
  - listRfpInternalDocuments
  - getRfpSuppliers
  - listRfpRecipientsHistory
  - listRfpPastEvents
  - getRfpLeadSource
  - getRfpLeadSourceSection
  - createProposalDraft
base_url: https://api-platform.cvent.com/ea
scopes:
  - rfp/rfps:read
  - rfp/rfp-agenda-items:read
  - rfp/rfp-guest-rooms:read
  - rfp/rfp-questions:read
  - rfp/rfp-custom-fields:read
  - rfp/rfp-attachments:read
  - rfp/rfp-internal-documents:read
  - rfp/rfp-suppliers:read
  - rfp/rfp-recipients-history:read
  - rfp/rfp-past-events:read
  - rfp/rfp-lead-sources:read
  - proposal/proposals:write
---

# Read an RFP and everything hanging off it

The RFP surface is almost entirely read-only — twelve of its fourteen operations are GETs. Treat it as
a source of record you mirror, not a system you drive.

## The RFP itself

`getRFP` — `GET /rfps/{rfpId}`. Returns the `RfpRequest`, including `preferredVenueIntegrations`
(`VenueIntegrationType`: CED, PASSKEY) which tells you which downstream Cvent systems the planner
expects the winning venue to be wired into.

## The requirements, one call per facet

| What | Operation | Path |
|---|---|---|
| Agenda | `listRfpAgendaItems` | `GET /rfps/{rfpId}/agenda-items` |
| Agenda schedules | `listRfpAgendaItemSchedules` | `GET /rfps/{rfpId}/agenda-items/schedules` |
| Guest rooms | `getRfpGuestRooms` | `GET /rfps/{rfpId}/guest-rooms` |
| Questions | `listRfpQuestions` | `GET /rfps/{rfpId}/questions` |
| Custom field answers | `listRfpCustomFields` | `GET /rfps/{rfpId}/custom-fields/answers` |
| Attachments | `listRfpAttachments` | `GET /rfps/{rfpId}/attachments` |
| Internal documents | `listRfpInternalDocuments` | `GET /rfps/{rfpId}/internal-documents` |

Internal documents are internal to the planner's account. Do not surface them to a supplier-facing
integration.

## Who it went to, and what happened before

- `getRfpSuppliers` — `GET /rfps/{rfpId}/suppliers`
- `listRfpRecipientsHistory` — `GET /rfps/{rfpId}/recipients/history`
- `listRfpPastEvents` — `GET /rfps/{rfpId}/past-events`, the planner's history with this programme
- `getRfpLeadSource` / `getRfpLeadSourceSection` — `GET /rfps/lead-sources/{leadSourceId}` and
  `/sections/{leadSourceSectionId}`, for attributing where the lead came from

## The one write

`createProposalDraft` — `POST /proposal-drafts`. **There is no delete, no update and no idempotency
key.** A retried POST creates a second draft, and nothing in the public contract takes it back. Confirm
the response before any retry, and never retry blind on a timeout.

## Runtime rules

Cursor pagination on `paging.currentToken`; `{code, message, details[]}` error envelope;
`X-RateLimit-*` headers with a 429 and no `Retry-After`. Signature documents for a signed contract are
read separately via `getSignatures` — `GET /signatures` (`onsite/signatures:read`).
