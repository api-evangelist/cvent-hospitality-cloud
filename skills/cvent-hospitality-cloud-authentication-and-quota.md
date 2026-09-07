---
name: cvent-authentication-and-quota
description: >-
  Get an access token for the Cvent REST API, verify it, and stay inside the account's rate limit and
  daily quota.
api: cvent-hospitality-cloud:authentication
generated: '2026-09-07'
method: generated
source: >-
  openapi/cvent-hospitality-cloud-authentication-openapi.yml,
  https://developers.cvent.com/docs/rest-api/tutorials/developer-quickstart,
  https://developers.cvent.com/docs/rest-api/guides/handling-rate-limits
operations:
  - oauth2Token
  - oauth2Authorize
  - validateToken
base_url: https://api-platform.cvent.com/ea
---

# Authenticate and stay inside the quota

## Get a token

Machine-to-machine integrations use client credentials; the call is attributed to the application.

1. Create a **Machine to Machine** application in a workspace on https://developers.cvent.com/ and
   attach only the scopes you need.
2. Base64-encode `client_id:client_secret` with no trailing newline.
3. `oauth2Token` — `POST /oauth2/token` with `Authorization: Basic <encoded>`.
4. Send the result as `Authorization: Bearer {accessToken}` on every call. **Tokens last 60 minutes.**

Web applications use `oauth2Authorize` — `GET /oauth2/authorize` (authorization code); the call is
attributed to the authenticating user, who must be both a Cvent admin and a registered developer.

`validateToken` — `GET /token-validation` verifies a token you already hold.

## The scope trap

Scopes are `<domain>/<resource>:<read|write|delete>` — 238 of them. A token carrying roughly 50 or
more returns **HTTP 431 Request headers too large**. Mint per-task tokens at runtime with only the
scopes that task needs. "Select All" on a workspace grants every current *and future* scope; use it
only if you mean it.

## Rate limits and quota

Limits are per account and depend on the account's usage tier. You do not have to guess:

- `getUsageTier` — `GET /usage/tier` returns the tier name, the **daily quota**, the **burst limit**
  and the **per-second steady rate**. A null quota means unlimited.
- `getUsage` — `GET /usage` returns the last seven days of call volume.

Every response carries `X-RateLimit-Limit`, `X-RateLimit-Remaining` and `X-RateLimit-Reset`. Read them
rather than waiting for the 429.

## Recovering from 429

There is **no `Retry-After` header**. Cvent's published strategy:

- **Per-second limit:** wait 2 seconds plus 1-1000 ms of jitter, double on each retry to a 16 second
  ceiling, give up after five attempts and log it.
- **Daily quota:** stop. Backoff does not help — wait until after midnight UTC.
- Either way, **every request counts against quota, including the ones that return 429**.

## Region

`https://api-platform.cvent.com/ea` (North America / global) or
`https://api-platform-eur.cvent.com/ea` (EU). An account lives in one region; the legacy SOAP API has
its own separate hosts and its own ticket-based login.
