# Auswide Bank (auswide-bank)

Auswide Bank Ltd is an Australian authorised deposit-taking institution (ADI) headquartered in Bundaberg, Queensland, offering home loans, savings and transaction accounts, term deposits, credit cards, and personal and business banking. Formerly Wide Bay Australia and previously ASX-listed (ABA), Auswide is now a division of MyState Bank Limited, a wholly owned subsidiary of the ASX-listed MyState Limited (ASX: MYS) following the 2025 merger. As an active CDR data holder under Australia's Consumer Data Right (Open Banking), Auswide exposes a public, unauthenticated Product Reference Data (PRD) API conforming to the DSB Consumer Data Standards.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/auswide-bank/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/auswide-bank/refs/heads/main/apis.yml)

## Tags

- Financial
- Banks
- Open Banking
- CDR
- Consumer Banking
- Australia
- Product Reference Data
- ADI

## Timestamps

- **Created:** 2026-07-20
- **Modified:** 2026-07-20

## APIs

### Auswide Bank CDR Product Reference Data API

Public, unauthenticated Consumer Data Right Product Reference Data (PRD) API exposing Auswide Bank's publicly available banking products (accounts, term deposits, home loans, credit cards) via the standard CDS endpoints `GET /banking/products` and `GET /banking/products/{productId}`. Confirmed live (HTTP 200, `x-v: 4`, 28 products) at the base URL below.

- **Human URL:** [https://www.auswidebank.com.au/help/banking-support/open-banking/](https://www.auswidebank.com.au/help/banking-support/open-banking/)
- **Base URL:** `https://api.auswidebank.com.au/openbanking/cds-au/v1`

#### Tags

- CDR
- Open Banking
- Product Reference Data
- Banking
- Australia

#### Properties

- [Documentation](https://www.auswidebank.com.au/help/banking-support/open-banking/)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#banking-apis)
- [OpenAPI](openapi/auswide-bank-cds-banking-products-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [Website](https://www.auswidebank.com.au/)
- [Documentation](https://www.auswidebank.com.au/help/banking-support/open-banking/)
- [LinkedIn](https://www.linkedin.com/company/auswide-bank-ltd/)
- [Privacy Policy](https://www.auswidebank.com.au/about/privacy-policy/)
- [Terms of Service](https://www.auswidebank.com.au/about/website-terms-of-use/)
- [Support](https://www.auswidebank.com.au/about/contact-us/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
