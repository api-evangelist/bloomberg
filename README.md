# Bloomberg (bloomberg)
Bloomberg delivers business and markets news, data, analysis, and video to the world, featuring stories from Businessweek and Bloomberg News. Bloomberg provides a suite of developer APIs including BLPAPI, Server API, and the Hypermedia API for programmatic access to market data, analytics, and enterprise services.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/bloomberg/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags:

 - Analytics, Business Intelligence, Data License, Enterprise, Execution Management, Financial Services, Market Data, News, Quantitative Analysis, Trading, Transaction Cost Analysis

## Timestamps

- **Created:** 2024-01-20
- **Modified:** 2026-04-18

## APIs

### Bloomberg Market Data API
Provides real-time and historical market data, including stock prices, indices, commodities, and currencies.

**Human URL:** [https://www.bloomberg.com/professional/support/api-library/](https://www.bloomberg.com/professional/support/api-library/)

#### Tags:

 - Financial Data, Indices, Market Data, Real-Time, Stocks

#### Properties

- [Documentation](https://www.bloomberg.com/professional/support/api-library/)
- [SDK](https://bloomberg.github.io/blpapi-docs/)

### Bloomberg Server API (SAPI)
Delivers real-time market data, historical data, reference data, and calculation engine capabilities from the Bloomberg Terminal for server applications.

**Human URL:** [https://www.bloomberg.com/professional/products/data/data-connectivity/server-api/](https://www.bloomberg.com/professional/products/data/data-connectivity/server-api/)

#### Tags:

 - Enterprise, Historical Data, Market Data, Real-Time, Reference Data, Server API

#### Properties

- [Documentation](https://www.bloomberg.com/professional/support/api-library/)
- [SDK](https://bloomberg.github.io/blpapi-docs/)

### Bloomberg Data License API
Provides programmatic access to Bloomberg Data License content including reference, pricing, regulatory, ESG, corporate actions, fundamentals, and alternative data.

**Human URL:** [https://www.bloomberg.com/professional/products/data/data-management/data-license/](https://www.bloomberg.com/professional/products/data/data-management/data-license/)

#### Tags:

 - Data License, Enterprise, ESG, Pricing Data, Reference Data, Regulatory Data

#### Properties

- [Documentation](https://www.bloomberg.com/professional/products/data/data-management/data-license/)

### Bloomberg EMSX API
Enables programmatic management and automation of equities, futures, and options trading through the Bloomberg Execution Management System.

**Human URL:** [https://www.bloomberg.com/professional/products/trading/execution-management-system/](https://www.bloomberg.com/professional/products/trading/execution-management-system/)

#### Tags:

 - Equities, Execution Management, Futures, Options, Orders, Trading

#### Properties

- [Documentation](https://emsx-api-doc.readthedocs.io/)

### Bloomberg BLPAPI Core
The Bloomberg Open API (BLPAPI) Core -- the foundational service-oriented, socket-based API used by the Desktop API, Server API (SAPI), B-PIPE, and Bloomberg Platform products.

**Human URL:** [https://www.bloomberg.com/professional/support/api-library/](https://www.bloomberg.com/professional/support/api-library/)

#### Tags:

 - B-PIPE, BLPAPI, Desktop API, Historical Data, Intraday Bars, Intraday Ticks, Market Data, Open API, Reference Data, Request Response, Server API, Subscription

#### Properties

- [Documentation](https://www.bloomberg.com/professional/support/api-library/)
- [SDK](https://bloomberg.github.io/blpapi-docs/)
- [OpenAPI](openapi/blpapi-core.yml)

## Common Properties

- [Portal](https://developer.bloomberg.com/)
- [Documentation](https://www.bloomberg.com/professional/support/api-library/)
- [SDK](https://bloomberg.github.io/blpapi-docs/)
- [GitHubOrganization](https://github.com/bloomberg)
- [GettingStarted](https://www.bloomberg.com/professional/solutions/asset-management/developer/)
- [Login](https://console.bloomberg.com/)
- [TermsOfService](https://www.bloomberg.com/notices/tos/)
- [PrivacyPolicy](https://www.bloomberg.com/privacy)
- [Support](https://www.bloomberg.com/professional/support/)

## Features

| Name | Description |
|------|-------------|
| Real-Time Market Data | Stream live market data for equities, fixed income, commodities, and currencies via subscription. |
| Historical Data | Access end-of-day historical time series with periodicity, currency, and corporate-action adjustments. |
| Intraday Tick Data | Retrieve raw tick-by-tick trade and quote data for granular intraday analysis. |
| Reference Data | Query current reference, descriptive, fundamental, and pricing field values for securities. |
| Field Discovery | Search and discover Bloomberg field mnemonics and metadata via the API Data Dictionary. |
| Multi-Language SDK | Access BLPAPI through C, C++, Java, .NET, Python, Perl, and COM Excel SDKs. |

## Use Cases

| Name | Description |
|------|-------------|
| Quantitative Research | Build quantitative models using historical and real-time market data for alpha generation. |
| Risk Management | Monitor portfolio risk exposure using real-time pricing and reference data feeds. |
| Algorithmic Trading | Feed market data into trading algorithms via EMSX for automated order execution. |
| Regulatory Reporting | Access regulatory and compliance data through Data License for reporting requirements. |

## Integrations

| Name | Description |
|------|-------------|
| Bloomberg Terminal | Extend Bloomberg Terminal capabilities through the Desktop API integration. |
| Excel | Access BLPAPI data directly from Excel spreadsheets using the COM Excel SDK. |
| Python | Build data analytics and machine learning pipelines with the Python BLPAPI SDK. |
| B-PIPE | Distribute Bloomberg data across enterprise infrastructure using the B-PIPE product. |

## Artifacts

Machine-readable API specifications organized by format.

### OpenAPI

- [BLPAPI Core OpenAPI](openapi/blpapi-core.yml)

### JSON Schema

- [BLPAPI Core Messages Schema](json-schema/blpapi-core-messages-schema.json)
- [Market Data Schema](json-schema/bloomberg-market-data-schema.json)
- [Security Schema](json-schema/bloomberg-security-schema.json)

### JSON-LD

- [Bloomberg Context](json-ld/bloomberg-context.jsonld)
- [BLPAPI Core Context](json-ld/blpapi-core-context.jsonld)

## Capabilities

Naftiko capabilities organized as shared per-API definitions composed into customer-facing workflows.

### Shared Per-API Definitions

- [Bloomberg BLPAPI Core](capabilities/shared/blpapi-core.yaml) — 9 operations for reference data, historical data, intraday analytics, and field discovery

### Workflow Capabilities

| Workflow | APIs Combined | Tools | Persona |
|----------|--------------|-------|---------|
| [Market Data](capabilities/market-data.yaml) | BLPAPI Core | 9 | Quantitative Analyst |

## Vocabulary

- [Bloomberg Vocabulary](vocabulary/bloomberg-vocabulary.yaml)

## Rules

- [Bloomberg Spectral Rules](rules/bloomberg-spectral-rules.yml)

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
