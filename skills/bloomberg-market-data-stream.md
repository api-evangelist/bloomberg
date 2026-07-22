---
name: Stream real-time market data
description: Subscribe to live quotes/trades, interval bars, and custom VWAP streams via the BLPAPI Subscription paradigm (//blp/mktdata, //blp/mktbar, //blp/mktvwap).
api: openapi/bloomberg-subscriptions-api-openapi.yml
operations: [subscribeMarketData, subscribeMarketBar, subscribeMarketVwap]
generated: '2026-06-20'
method: generated
---

# Stream real-time market data

Open a BLPAPI SDK session (see `authentication/bloomberg-authentication.yml`). The Subscription
paradigm pushes SUBSCRIPTION_DATA events over the session — the event surface is described in
`asyncapi/bloomberg-market-data-asyncapi.yml`.

## Steps

1. **Build a SubscriptionList.** Each entry names a `service` + `topic` (e.g. `"IBM US Equity"`),
   the `fields[]` to stream (e.g. LAST_PRICE, BID, ASK), optional `options`, and a unique
   `correlationId`.
2. **Subscribe.** Use `subscribeMarketData` (`//blp/mktdata`) for live quotes/trades,
   `subscribeMarketBar` (`//blp/mktbar`) for interval OHLC bars, or `subscribeMarketVwap`
   (`//blp/mktvwap`) with override field/value pairings for a custom VWAP stream.
3. **Confirm startup.** Watch SUBSCRIPTION_STATUS: `SubscriptionStarted` may carry per-field
   `exceptions[]`; `SubscriptionFailure` carries a `reason` — fix the topic or entitlements and
   resubscribe (see `errors/bloomberg-problem-types.yml`).
4. **Consume the stream.** SUBSCRIPTION_DATA events deliver MarketDataEvents keyed by your
   CorrelationID; `IS_DELAYED_STREAM` tells you if the feed is delayed rather than real-time.
5. **Unsubscribe** with the same CorrelationIDs when done to release capacity.

## Rules

- Subscription capacity is limited per product/entitlement (`rate-limits/bloomberg-rate-limits.yml`);
  batch topics into one SubscriptionList instead of many sessions.
- Treat delayed streams (`IS_DELAYED_STREAM: true`) as non-real-time in downstream logic.
- There are no webhooks: streaming exists only over the live SDK session.
