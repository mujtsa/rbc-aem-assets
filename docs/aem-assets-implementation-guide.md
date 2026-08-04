# RBC AEM Assets Implementation Guide

## Purpose

This document describes the implementation of AEM Assets for the RBC Edge Delivery Services demonstration.

The implementation is initially validated using the local AEM as a Cloud Service SDK and will later be configured in an Adobe cloud environment.

## Demo Scope

The demonstration covers these RBC reference pages:

* All Credit Cards
  `https://www.rbcroyalbank.com/credit-cards/all-credit-cards.html`

* GIC Overview
  `https://www.rbcroyalbank.com/investments/gics.html`

## Target Architecture

AEM Assets
→ Metadata and governance
→ Asset review and approval
→ Asset publishing or Dynamic Media delivery
→ DA.live asset selection
→ AEM Edge Delivery Services
→ Preview and production publishing

## Local Environment

| Component              | Location                       |
| ---------------------- | ------------------------------ |
| AEM Author             | `http://localhost:4502`        |
| AEM Publish            | `http://localhost:4503`        |
| Maven repository       | `C:\POC\rbc-aem-assets`        |
| EDS repository         | Separate EDS GitHub repository |
| App Builder repository | Separate backend repository    |

## Completed Activities

* Downloaded and started the AEM as a Cloud Service SDK.
* Configured local Author on port `4502`.
* Configured local Publish on port `4503`.
* Enabled local Author-to-Publish replication.
* Published and validated a sample DAM asset.
* Generated the `rbc-aem-assets` Maven repository.
* Included Dispatcher configuration.
* Installed Adobe AEM Cloud Service Claude skills.
* Added repository-specific `CLAUDE.md` instructions.

## Planned DAM Structure

```text
/content/dam/rbc-eds-demo
├── shared
│   └── brand
├── cards
│   ├── product-images
│   ├── promotional
│   └── documents
└── gic
    ├── benefits
    ├── tools
    └── documents
```

## Planned Governance

The implementation will include:

* RBC-specific DAM folders
* Role-based permissions
* RepoInit-managed groups and ACLs
* Folder-specific metadata schemas
* Asset review and approval
* Rights and expiry metadata
* Author-to-Publish validation
* EDS asset-selection integration

## Planned Security Groups

| Group               | Responsibility                                     |
| ------------------- | -------------------------------------------------- |
| `rbc-dam-authors`   | Upload and update assets and metadata              |
| `rbc-dam-reviewers` | Review, approve and publish assets                 |
| `rbc-dam-admins`    | Manage schemas, workflows, folders and permissions |

## Cloud-Only Activities

The following require an AEM as a Cloud Service environment:

* Adobe IMS and product-profile configuration
* DA.live AEM Assets picker
* Dynamic Media with OpenAPI
* Cloud Asset Compute processing
* Cloud Manager deployment
* Production CDN and Dispatcher validation