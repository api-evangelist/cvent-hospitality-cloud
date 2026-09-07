# Cvent Hospitality Cloud (cvent-hospitality-cloud)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Cvent Hospitality Cloud is the hotel and venue product line of the Cvent Platform. It includes the Cvent Supplier Network (the marketplace connecting event planners with hotels and venues for RFPs and bookings), Passkey (hotel room block and housing management), Venue Sourcing (venue search and discovery), and Sales & Catering (booking management, catering, and contracts). Programmatic access is delivered primarily through the Passkey RegLink REST APIs (with legacy SOAP and URL-based options) and the unified Cvent Platform REST API. Authentication uses OAuth 2.0 client credentials with the token endpoint at api-platform.cvent.com/ea/oauth2/token.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/cvent-hospitality-cloud/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/cvent-hospitality-cloud/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consuming
- **Access:** 3rd-Party

## Tags

- Catering
- Group Bookings
- Hospitality
- Hospitality Cloud
- Hotels
- Housing
- Authentication
- Passkey
- Reservations
- RFP
- Room Blocks
- Sales
- Sourcing
- Supplier Network
- Venues

## Timestamps

- **Created:** 2024-01-01
- **Modified:** 2026-09-07

## APIs

### Cvent Passkey RegLink API

Passkey RegLink is the hotel room-block and housing surface of the Cvent platform. It connects an external registration system to Passkey events and hotel inventory: fetch housing events, hotels, room types, availability and inventory; create a reservation request (the "bridge") that pre-populates a registrant and hands them a unique booking link; then create, update, cancel, link and unlink the resulting reservations. Cvent's own migration guide maps every legacy XML and browser RegLink call onto these operations. It is delivered as the Housing and Housing Hotels tags of the unified Cvent REST API at https://api-platform.cvent.com/ea, secured with OAuth 2.0 and 15 housing/* scopes, with an optional callback service that POSTs on reservation create, modify and cancel. Passkey is an add-on licence.

- **Human URL:** [https://developers.cvent.com/docs/passkey/REST/overview](https://developers.cvent.com/docs/passkey/REST/overview)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- Group Bookings
- Hotel
- Passkey
- Reservations
- Room Blocks
- Housing

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-housing-openapi.yml)
- [Open API](openapi/cvent-hospitality-cloud-housing-hotels-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-housing-overlay.yaml)
- [Documentation](https://developers.cvent.com/docs/passkey/REST/overview)
- [Getting Started](https://developers.cvent.com/docs/passkey/REST/getting-started)
- [Migration](https://developers.cvent.com/docs/passkey/REST/migration)
- [Webhooks](https://developers.cvent.com/docs/passkey/REST/callbacks)
- [Webhooks](asyncapi/cvent-hospitality-cloud-webhooks.yml)
- [Agent Skill](skills/cvent-hospitality-cloud-reglink-room-block-booking.md)
- [Agent Skill](skills/cvent-hospitality-cloud-housing-reservation-management.md)
- [Data Model](https://developers.cvent.com/docs/platform/data-models/housing)
- [Product](https://www.cvent.com/en/supplier-venue/passkey)

### Cvent Platform REST API (Hospitality)

The unified Cvent REST API at https://api-platform.cvent.com/ea (and its EMEA peer https://api-platform-eur.cvent.com/ea) is one OpenAPI 3.0.2 document of 356 paths and 469 operations across 56 tags; 87 of those operations are the hospitality surface split into this repository. Authentication is OAuth 2.0 — client credentials for machine-to-machine applications, authorization code for web applications — with 238 named scopes, 60-minute tokens, cursor pagination on paging.currentToken, a {code, message, details[]} error envelope, X-RateLimit-* headers and a per-account usage tier readable at GET /usage/tier.

- **Human URL:** [https://developers.cvent.com/docs/rest-api/overview](https://developers.cvent.com/docs/rest-api/overview)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- Event
- Authentication
- REST
- Webhook
- Platform

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-authentication-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-authentication-overlay.yaml)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)
- [API Reference](https://developers.cvent.com/documentation)
- [Getting Started](https://developers.cvent.com/docs/rest-api/tutorials/developer-quickstart)
- [Concepts](https://developers.cvent.com/docs/rest-api/explanation/concepts)
- [Change Log](https://developers.cvent.com/docs/rest-api/changelog)
- [Authentication](authentication/cvent-hospitality-cloud-authentication.yml)
- [OAuth Scopes](scopes/cvent-hospitality-cloud-scopes.yml)
- [Rate Limits](rate-limits/cvent-hospitality-cloud-rate-limits.yml)
- [Agent Skill](skills/cvent-hospitality-cloud-authentication-and-quota.md)
- [OAuth Token Endpoint](https://api-platform.cvent.com/ea/oauth2/token)

### Cvent SOAP Web Services API (V200611)

Cvent's legacy SOAP 1.1 / WSDL 1.1 / WS-I Basic Profile 1.1 Web Services API, still served and still documented. 51 operations and 390 complex types under targetNamespace http://api.cvent.com/2006-11, including the hospitality calls CreateRFP, CreateMeetingRequest, UpdateMeetingRequest and the approver operations. Authentication is a session ticket obtained from its own Login call — not OAuth. Quota is 10,000 calls per organization per 24 hours (Eastern Time), introspectable via DescribeGlobal. Cvent files it under legacy-api and publishes a call-by-call REST migration guide, but has announced no sunset.

- **Human URL:** [https://developers.cvent.com/docs/legacy-api/soap-api/framework](https://developers.cvent.com/docs/legacy-api/soap-api/framework)
- **Base URL:** `https://api.cvent.com/soap/V200611.ASMX`

#### Tags

- SOAP
- Legacy
- RFP
- Meeting Requests

#### Properties

- [W S D L](wsdl/cvent-hospitality-cloud-soap-v200611.wsdl)
- [Documentation](https://developers.cvent.com/docs/legacy-api/soap-api/framework)
- [API Reference](https://developers.cvent.com/docs/legacy-api/soap-api/call-definitions/overview)
- [Error Catalog](https://developers.cvent.com/docs/legacy-api/soap-api/error-codes)
- [Change Log](https://developers.cvent.com/docs/legacy-api/soap-api/changelog)
- [Migration](https://developers.cvent.com/docs/rest-api/migration-guide/calls-and-methods)

### Cvent RFP Management API

Read a Cvent Supplier Network RFP and its lead sources. Delivered as the RFP Management tag of the unified Cvent REST API — 3 operation(s) at https://api-platform.cvent.com/ea, OAuth 2.0 secured.

- **Human URL:** [https://developers.cvent.com/documentation](https://developers.cvent.com/documentation)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- RFP
- Sourcing
- Supplier Network

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-rfp-management-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-rfp-management-overlay.yaml)
- [API Reference](https://developers.cvent.com/documentation)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)

### Cvent RFP Requirements API

The requirements attached to an RFP — agenda items and schedules, guest rooms, questions, custom-field answers, attachments and internal documents. Delivered as the RFP Requirements tag of the unified Cvent REST API — 7 operation(s) at https://api-platform.cvent.com/ea, OAuth 2.0 secured.

- **Human URL:** [https://developers.cvent.com/documentation](https://developers.cvent.com/documentation)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- RFP
- Sourcing
- Guest Rooms

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-rfp-requirements-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-rfp-requirements-overlay.yaml)
- [API Reference](https://developers.cvent.com/documentation)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)

### Cvent RFP Suppliers API

The suppliers an RFP was sent to and the history of those recipients. Delivered as the RFP Suppliers tag of the unified Cvent REST API — 2 operation(s) at https://api-platform.cvent.com/ea, OAuth 2.0 secured.

- **Human URL:** [https://developers.cvent.com/documentation](https://developers.cvent.com/documentation)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- RFP
- Supplier Network
- Hotels

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-rfp-suppliers-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-rfp-suppliers-overlay.yaml)
- [API Reference](https://developers.cvent.com/documentation)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)

### Cvent RFP Additional Details API

A planner’s past-event history for an RFP. Delivered as the RFP Additional Details tag of the unified Cvent REST API — 1 operation(s) at https://api-platform.cvent.com/ea, OAuth 2.0 secured.

- **Human URL:** [https://developers.cvent.com/documentation](https://developers.cvent.com/documentation)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- RFP
- Sourcing

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-rfp-additional-details-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-rfp-additional-details-overlay.yaml)
- [API Reference](https://developers.cvent.com/documentation)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)

### Cvent Proposal Draft API

Create a draft proposal in response to an RFP. Delivered as the Proposal Draft tag of the unified Cvent REST API — 1 operation(s) at https://api-platform.cvent.com/ea, OAuth 2.0 secured.

- **Human URL:** [https://developers.cvent.com/documentation](https://developers.cvent.com/documentation)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- Proposals
- Supplier Network
- Hotels

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-proposal-drafts-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-proposal-drafts-overlay.yaml)
- [API Reference](https://developers.cvent.com/documentation)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)

### Cvent Venue Profiles API

Maintain a venue profile — type, contact, address and facility details. Both replace (PUT) and merge (PATCH) are offered. Delivered as the Venue Profiles tag of the unified Cvent REST API — 5 operation(s) at https://api-platform.cvent.com/ea, OAuth 2.0 secured.

- **Human URL:** [https://developers.cvent.com/documentation](https://developers.cvent.com/documentation)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- Venues
- Hotels
- Sourcing

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-venue-profiles-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-venue-profiles-overlay.yaml)
- [API Reference](https://developers.cvent.com/documentation)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)

### Cvent Venue Meeting Rooms API

Create and maintain a venue’s meeting rooms, their capacities and amenities, and the images associated with them. Delivered as the Venue Meeting Rooms tag of the unified Cvent REST API — 8 operation(s) at https://api-platform.cvent.com/ea, OAuth 2.0 secured.

- **Human URL:** [https://developers.cvent.com/documentation](https://developers.cvent.com/documentation)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- Venues
- Meeting Rooms
- Catering

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-venue-meeting-rooms-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-venue-meeting-rooms-overlay.yaml)
- [API Reference](https://developers.cvent.com/documentation)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)

### Cvent Meeting Request API

Meeting request forms and the requests submitted against them, plus the documents attached to a request. Delivered as the Meeting Request tag of the unified Cvent REST API — 8 operation(s) at https://api-platform.cvent.com/ea, OAuth 2.0 secured.

- **Human URL:** [https://developers.cvent.com/documentation](https://developers.cvent.com/documentation)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- Meeting Requests
- Sourcing
- Event

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-meeting-requests-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-meeting-requests-overlay.yaml)
- [API Reference](https://developers.cvent.com/documentation)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)

### Cvent Travel RFPs API

Business-transient travel programs, their questions, and the proposals and bids submitted against them. Delivered as the Travel RFPs tag of the unified Cvent REST API — 9 operation(s) at https://api-platform.cvent.com/ea, OAuth 2.0 secured.

- **Human URL:** [https://developers.cvent.com/documentation](https://developers.cvent.com/documentation)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- Business Travel
- RFP
- Hotels

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-travel-rfps-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-travel-rfps-overlay.yaml)
- [API Reference](https://developers.cvent.com/documentation)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)

### Cvent Travel Suppliers API

The hotel supplier directory behind business travel sourcing — chains, brands, properties and property rooms. Delivered as the Travel Suppliers tag of the unified Cvent REST API — 8 operation(s) at https://api-platform.cvent.com/ea, OAuth 2.0 secured.

- **Human URL:** [https://developers.cvent.com/documentation](https://developers.cvent.com/documentation)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- Business Travel
- Hotels
- Supplier Network

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-travel-suppliers-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-travel-suppliers-overlay.yaml)
- [API Reference](https://developers.cvent.com/documentation)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)

### Cvent Travel Accounts API

Travel accounts and the supplier accounts beneath them. Delivered as the Travel Accounts tag of the unified Cvent REST API — 4 operation(s) at https://api-platform.cvent.com/ea, OAuth 2.0 secured.

- **Human URL:** [https://developers.cvent.com/documentation](https://developers.cvent.com/documentation)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- Business Travel
- Accounts

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-travel-accounts-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-travel-accounts-overlay.yaml)
- [API Reference](https://developers.cvent.com/documentation)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)

### Cvent Event Travel API

Air requests and actuals, hotel requests and housing reservation requests attached to an event. Delivered as the Event Travel tag of the unified Cvent REST API — 5 operation(s) at https://api-platform.cvent.com/ea, OAuth 2.0 secured.

- **Human URL:** [https://developers.cvent.com/documentation](https://developers.cvent.com/documentation)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- Event
- Travel
- Housing

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-event-travel-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-event-travel-overlay.yaml)
- [API Reference](https://developers.cvent.com/documentation)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)

### Cvent Signatures API

Signature documents produced by the onsite/contracting surface. Delivered as the Signatures tag of the unified Cvent REST API — 1 operation(s) at https://api-platform.cvent.com/ea, OAuth 2.0 secured.

- **Human URL:** [https://developers.cvent.com/documentation](https://developers.cvent.com/documentation)
- **Base URL:** `https://api-platform.cvent.com/ea`

#### Tags

- Contracts
- Signatures

#### Properties

- [Open API](openapi/cvent-hospitality-cloud-signatures-openapi.yml)
- [Overlay](overlays/cvent-hospitality-cloud-signatures-overlay.yaml)
- [API Reference](https://developers.cvent.com/documentation)
- [Documentation](https://developers.cvent.com/docs/rest-api/overview)

## Common Properties

- [Agentic Access](agentic-access/cvent-hospitality-cloud-agentic-access.yml)
- [Trust Center](security/cvent-hospitality-cloud-trust-center.yml)
- [Domain Security](security/cvent-hospitality-cloud-domain-security.yml)
- [Authentication](authentication/cvent-hospitality-cloud-authentication.yml)
- [OAuth Scopes](scopes/cvent-hospitality-cloud-scopes.yml)
- [Git Hub Organization](https://github.com/cvent)
- [Developer Portal](https://developers.cvent.com/)
- [Support](https://support.cvent.com/)
- [Status Page](https://status.cvent.com/)
- [Privacy Policy](https://www.cvent.com/en/privacy-policy)
- [Blog](https://www.cvent.com/en/blog/feed.xml)
- [Website](https://www.cvent.com/en/supplier-venue)
- [Supplier Network](https://www.cvent.com/venues)
- [Passkey](https://www.cvent.com/en/supplier-venue/passkey)
- [Terms Of Service](https://www.cvent.com/en/product-terms-of-use)
- [Documentation](https://developers.cvent.com/docs)
- [API Reference](https://developers.cvent.com/documentation)
- [Getting Started](https://developers.cvent.com/docs/rest-api/tutorials/developer-quickstart)
- [Sign Up](https://developers.cvent.com/signup)
- [Login](https://developers.cvent.com/login)
- [Blog](https://www.cvent.com/en/blog/latest)
- [Trust Center](https://trust.cvent.com/)
- [Compliance](conformance/cvent-hospitality-cloud-conformance.yml)
- [Conformance](conformance/cvent-hospitality-cloud-conformance.yml)
- [M C P Server](mcp/cvent-hospitality-cloud-mcp.yml)
- [Tool Crosswalk](mcp/cvent-hospitality-cloud-tool-crosswalk.yml)
- [Packages](packages/cvent-hospitality-cloud-packages.yml)
- [SDKs](packages/cvent-hospitality-cloud-packages.yml)
- [Well Known](well-known/cvent-hospitality-cloud-well-known.yml)
- [L L Ms Txt](llms/cvent-hospitality-cloud-llms.txt)
- [Llms Text](https://www.cvent.com/llms.txt)
- [W S D L](wsdl/cvent-hospitality-cloud-soap-v200611.wsdl)
- [Error Catalog](errors/cvent-hospitality-cloud-problem-types.yml)
- [Lifecycle](lifecycle/cvent-hospitality-cloud-lifecycle.yml)
- [Change Log](changelog/cvent-hospitality-cloud-changelog.yml)
- [Conventions](conventions/cvent-hospitality-cloud-conventions.yml)
- [Data Model](data-model/cvent-hospitality-cloud-data-model.yml)
- [Sandbox](sandbox/cvent-hospitality-cloud-sandbox.yml)
- [Webhooks](asyncapi/cvent-hospitality-cloud-webhooks.yml)
- [Agent Skill](skills/_index.yml)
- [Rate Limits](rate-limits/cvent-hospitality-cloud-rate-limits.yml)
- [Plans](plans/cvent-hospitality-cloud-plans-pricing.yml)
- [Support](https://www.cvent.com/en/contact/support)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
