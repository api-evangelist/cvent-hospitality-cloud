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
- OAuth 2.0
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
- **Modified:** 2026-04-28

## APIs

### Cvent Passkey RegLink API

Passkey RegLink APIs are RESTful JSON APIs (with legacy URL-based and SOAP options) that connect Cvent registration with Passkey hotel reservations. Primary functions include sending registrant information to Passkey to streamline hotel reservations, fetching Passkey event and hotel availability, retrieving reservation information, and creating, updating, and cancelling registrant reservations.

- **Human URL:** [https://developers.cvent.com/docs/passkey/REST/overview](https://developers.cvent.com/docs/passkey/REST/overview)
- **Base URL:** `https://api-platform.cvent.com`

#### Tags

- Group Bookings
- Hotel
- Passkey
- Reservations
- Room Blocks

#### Properties

- [Documentation](https://developers.cvent.com/docs/passkey/REST/overview)
- [Getting Started](https://developers.cvent.com/docs/passkey/REST/getting-started)
- [Passkey Docs](https://developers.cvent.com/doc/passkey/)
- [Product](https://www.cvent.com/en/hospitality-cloud/passkey)
- [Postman Collection](collections/cvent-hospitality-cloud.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/cvent-hospitality-cloud.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Cvent Platform REST API (Hospitality)

The unified Cvent Platform REST API also covers hospitality use cases including event-driven integrations, contact and attendee data exchange, and webhook-based notifications that can be wired into hotel and venue workflows. OAuth 2.0 client credentials.

- **Human URL:** [https://developers.cvent.com/docs/rest-api/overview](https://developers.cvent.com/docs/rest-api/overview)
- **Base URL:** `https://api-platform.cvent.com`

#### Tags

- Events
- OAuth 2.0
- REST
- Webhooks

#### Properties

- [Documentation](https://developers.cvent.com/docs/rest-api/overview)
- [Concepts](https://developers.cvent.com/docs/rest-api)
- [O Auth Token Endpoint](https://api-platform.cvent.com/ea/oauth2/token)
- [Postman Collection](collections/cvent-hospitality-cloud.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/cvent-hospitality-cloud.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [GitHub Organization](https://github.com/cvent)
- [Website](https://www.cvent.com/en/hospitality-cloud)
- [Supplier Network](https://www.cvent.com/en/hospitality-cloud/event-management/cvent-supplier-network)
- [Passkey](https://www.cvent.com/en/hospitality-cloud/passkey)
- [Developer Portal](https://developers.cvent.com/)
- [Support](https://support.cvent.com/)
- [Status Page](https://status.cvent.com/)
- [Terms of Service](https://www.cvent.com/en/terms-of-service)
- [Privacy Policy](https://www.cvent.com/en/privacy-policy)
- [L L Ms Txt](https://www.cvent.com/llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
