---
name: Look up reference data for securities
description: Get current reference, descriptive, fundamental, and pricing field values for one or more securities via BLPAPI //blp/refdata, discovering field mnemonics first when needed.
api: openapi/bloomberg-reference-data-api-openapi.yml
operations: [referenceDataRequest, fieldSearchRequest, fieldInfoRequest]
generated: '2026-06-20'
method: generated
---

# Look up reference data for securities

BLPAPI is a socket/SDK API, not REST: open a BLPAPI SDK session (Desktop API `localhost:8194`
inherits the terminal login; SAPI/B-PIPE requires `//blp/apiauth` authorization — see
`authentication/bloomberg-authentication.yml`), then open the `//blp/refdata` service.

## Steps

1. **Discover fields if you only know the concept, not the mnemonic.** Use `fieldSearchRequest`
   (`//blp/apiflds`) with a `searchSpec` like `"last price"`; inspect candidates, then confirm
   details with `fieldInfoRequest` (set `returnFieldDocumentation: true`).
2. **Build the request.** Call `referenceDataRequest` with `securities[]` (topic strings such as
   `"IBM US Equity"`) and `fields[]` (mnemonics such as `PX_LAST`, `SECURITY_NAME`). Use
   `overrides[]` only for documented override field/value pairs.
3. **Correlate and collect.** Tag the request with a CorrelationID; consume PARTIAL_RESPONSE events
   until the final RESPONSE event arrives (see `conventions/bloomberg-conventions.yml`).
4. **Handle partial failures.** A successful response can still carry per-security `securityError`
   (BAD_SEC — fix the ticker/yellow key) and per-field `fieldExceptions` (BAD_FLD — rediscover the
   mnemonic). Request-level failures arrive as `responseError`; LIMIT category means a daily or
   concurrent cap was hit (`errors/bloomberg-problem-types.yml`).

## Rules

- Never invent field mnemonics — resolve them through `fieldSearchRequest`/`fieldInfoRequest`.
- Respect entitlements: data returns only for fields/securities the session identity is entitled to.
- No pagination: responses are complete; do not poll for more pages.
