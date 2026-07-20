---
name: Look up Auswide Bank banking products
description: >-
  Discover Auswide Bank's publicly available banking products (accounts, term
  deposits, home loans, credit cards) and retrieve full product detail — rates,
  fees, features, eligibility and constraints — via the public, unauthenticated
  CDR Product Reference Data API. No credentials or consent required.
api: openapi/auswide-bank-cds-banking-products-openapi.yml
operations:
- listBankingProducts
- getBankingProductDetail
---

# Look up Auswide Bank banking products

Auswide Bank's Product Reference Data (PRD) endpoints are **public and
unauthenticated**. The only access control is API version negotiation via the
mandatory `x-v` request header. Base URL:
`https://api.auswidebank.com.au/openbanking/cds-au/v1`.

## Rules

- Always send the `x-v` request header. For `listBankingProducts` the currently
  served version is `4`; for `getBankingProductDetail` it is `7`. Omitting it or
  requesting an unsupported version returns `406` with a
  `urn:au-cds:error:cds:all:header:invalid-version` error and an `Available` list.
- No `Authorization` header, API key, or consent is needed for these two
  operations. (All other CDR banking endpoints require ADR accreditation + MTLS +
  consumer consent — out of scope for this skill.)
- Responses wrap `{ data, links, meta }`. Errors use the CDS envelope
  `{ "errors": [ { "code", "title", "detail", "meta" } ] }` — see
  `errors/auswide-bank-problem-types.yml`.

## Steps

1. **List products** — call `listBankingProducts`
   (`GET /banking/products`) with header `x-v: 4`. Optionally filter with
   `effective` (`CURRENT` | `FUTURE` | `ALL`, default `CURRENT`),
   `product-category` (e.g. `RESIDENTIAL_MORTGAGES`, `TERM_DEPOSITS`,
   `TRANS_AND_SAVINGS_ACCOUNTS`, `CRED_AND_CHRG_CARDS`), `brand`, and
   `updated-since`. Page with `page` / `page-size`; read `meta.totalRecords` and
   `meta.totalPages`, and follow `links.next` until absent.

2. **Pick a product** — each item in `data.products` carries a `productId`,
   `productCategory`, `name`, and `description`.

3. **Get full detail** — call `getBankingProductDetail`
   (`GET /banking/products/{productId}`) with header `x-v: 7`, passing the
   `productId` from step 2. The response's `data` (BankingProductDetailV7) includes
   `features`, `constraints`, `eligibility`, `fees`, `depositRates`,
   `lendingRates`, `bundles`, and `instalments`. A `404`
   (`urn:au-cds:error:cds:banking:product:invalid`) means the `productId` is not
   valid.

## Notes

- Product `productId` values are data-holder-specific and not permanence
  guaranteed — always re-list rather than caching ids long-term.
- See `conventions/auswide-bank-conventions.yml` for pagination and versioning
  details.
