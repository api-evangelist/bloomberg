---
name: Pull historical and intraday time series
description: Retrieve end-of-day history, intraday OHLC bars, and raw ticks for securities via BLPAPI //blp/refdata for backtesting and analysis.
api: openapi/bloomberg-historical-data-api-openapi.yml
operations: [historicalDataRequest, intradayBarRequest, intradayTickRequest]
generated: '2026-06-20'
method: generated
---

# Pull historical and intraday time series

Open a BLPAPI SDK session (see `authentication/bloomberg-authentication.yml`) and the
`//blp/refdata` service.

## Steps

1. **End-of-day history.** Call `historicalDataRequest` with `securities[]`, `fields[]`,
   `startDate`/`endDate`, and `periodicitySelection` (DAILY/WEEKLY/MONTHLY...). Control adjustments
   with `periodicityAdjustment`, `currency`, `pricingOption`, and the non-trading-day fill options;
   bound result size with `maxDataPoints`.
2. **Intraday bars.** Call `intradayBarRequest` with a single `security`, an `eventType` (e.g.
   TRADE), `interval` (minutes), and `startDateTime`/`endDateTime`. Corporate-action behavior is
   controlled by the `adjustmentNormal`/`adjustmentAbnormal`/`adjustmentSplit` flags.
3. **Raw ticks.** Call `intradayTickRequest` with a single `security`, `eventTypes[]`, and a
   `startDateTime`/`endDateTime` window; enable `includeConditionCodes`/`includeExchangeCodes` when
   you need venue detail.
4. **Correlate and collect.** Consume PARTIAL_RESPONSE events until RESPONSE, keyed by your
   CorrelationID; handle `responseError`, `securityError`, and `fieldExceptions` per
   `errors/bloomberg-problem-types.yml`.

## Rules

- Intraday operations take exactly one security per request — batch by issuing multiple requests.
- Keep date windows tight: LIMIT-category errors signal entitlement/data caps
  (`rate-limits/bloomberg-rate-limits.yml`).
- Timestamps are UTC unless the request says otherwise; be explicit when comparing sessions.
