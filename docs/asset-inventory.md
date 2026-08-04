# RBC Demo Asset Inventory

## Reference Pages

### All Credit Cards

`https://www.rbcroyalbank.com/credit-cards/all-credit-cards.html`

### GIC Overview

`https://www.rbcroyalbank.com/investments/gics.html`

## Shared Assets

| Asset                  | DAM location                                 |  Required |
| ---------------------- | -------------------------------------------- | --------: |
| RBC logo               | `/content/dam/rbc-eds-demo/shared/brand`     |       Yes |
| Shared legal documents | `/content/dam/rbc-eds-demo/shared/documents` | As needed |

## Credit-Card Assets

| Asset type          | Proposed DAM location                            | Required |
| ------------------- | ------------------------------------------------ | -------: |
| Card artwork        | `/content/dam/rbc-eds-demo/cards/product-images` |      Yes |
| Promotional imagery | `/content/dam/rbc-eds-demo/cards/promotional`    | Optional |
| Product guides      | `/content/dam/rbc-eds-demo/cards/documents`      | Optional |
| Small UI icons      | EDS GitHub repository                            |      Yes |

The first demonstration will use approximately six to eight representative cards rather than the complete catalogue.

## GIC Assets

| Asset type           | Proposed DAM location                     |  Required |
| -------------------- | ----------------------------------------- | --------: |
| Benefit icons        | `/content/dam/rbc-eds-demo/gic/benefits`  |       Yes |
| Tool illustrations   | `/content/dam/rbc-eds-demo/gic/tools`     |       Yes |
| Agreements and PDFs  | `/content/dam/rbc-eds-demo/gic/documents` |  Optional |
| Small fixed UI icons | EDS GitHub repository                     | As needed |

## Dynamic Data

The following values must not be stored as DAM images:

* Credit-card annual fees
* Purchase rates
* Cash-advance rates
* Welcome offers
* Product eligibility
* GIC rates
* Effective dates
* Apply URLs

These values will come from structured content or published APIs.