# Cvent Hospitality Cloud (cvent-hospitality-cloud)

Cvent Hospitality Cloud is the hotel and venue product line of the Cvent Platform. It includes the Cvent Supplier Network (event planner / venue marketplace and RFP exchange), Passkey (hotel room block and housing management), Venue Sourcing, and Sales & Catering. Programmatic access is delivered primarily through the Passkey RegLink REST APIs (with legacy SOAP and URL-based options) and the unified Cvent Platform REST API, both authenticated via OAuth 2.0 client credentials.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/cvent-hospitality-cloud/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consuming
- **Access:** 3rd-Party
- **x-type:** company

## Tags

- Catering, Group Bookings, Hospitality, Hospitality Cloud, Hotels, Housing, OAuth 2.0, Passkey, Reservations, RFP, Room Blocks, Sales, Sourcing, Supplier Network, Venues

## Timestamps

- **Created:** 2024-01-01
- **Modified:** 2026-04-28

## APIs

### Cvent Passkey RegLink API

RESTful JSON APIs (with legacy URL-based and SOAP options) connecting Cvent registration with Passkey hotel reservations: send registrant information to Passkey, fetch event and hotel availability, retrieve reservation information, and create/update/cancel reservations.

**Human URL:** https://developers.cvent.com/docs/passkey/REST/overview
**Base URL:** `https://api-platform.cvent.com`

### Cvent Platform REST API (Hospitality)

The unified Cvent Platform REST API also covers hospitality-adjacent use cases via event, contact, attendee, and webhook resources that can be wired into hotel and venue workflows.

**Human URL:** https://developers.cvent.com/docs/rest-api/overview
**Base URL:** `https://api-platform.cvent.com`

## Capabilities

- Hotel room block and housing management (Passkey)
- Hotel reservation lifecycle: create, update, cancel
- Event-to-hotel availability lookup
- Venue sourcing and RFP integration through the Cvent Supplier Network
- Sales & Catering booking management

## Use Cases

- Drive hotel reservations from a third-party registration system
- Pipe Passkey reservation data into hotel PMS / CRM systems
- Integrate venue search and RFP workflows into planner platforms
- Sync event-housing rosters with revenue management systems

## Common Resources

- [Cvent Hospitality Cloud](https://www.cvent.com/en/hospitality-cloud)
- [Cvent Supplier Network](https://www.cvent.com/en/hospitality-cloud/event-management/cvent-supplier-network)
- [Passkey Product](https://www.cvent.com/en/hospitality-cloud/passkey)
- [Developer Portal](https://developers.cvent.com/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
