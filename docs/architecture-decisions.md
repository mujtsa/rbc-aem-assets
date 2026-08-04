# RBC AEM Assets Architecture Decisions

## ADR-001 — Separate Repositories

### Status

Accepted

### Decision

Maintain separate repositories for:

* AEM Assets configuration
* AEM Edge Delivery Services
* Adobe Developer App Builder

### Rationale

The repositories have different runtimes, deployment pipelines, security models and development conventions.

---

## ADR-002 — RepoInit for Permissions

### Status

Accepted

### Decision

Use RepoInit to create AEM groups and manage DAM permissions. Namespace registration resides in `config` (all tiers); groups, folders, and ACLs reside in `config.author` (Author only).

### Rationale

RepoInit provides repeatable, version-controlled and environment-consistent authorization configuration. Scoping to `config.author` prevents Publish from attempting to create unused Author groups.

---

## ADR-003 — Business Assets Excluded from Maven

### Status

Accepted

### Decision

Do not commit normal business asset binaries to the Maven repository.

### Rationale

Business assets should be uploaded, governed and versioned through AEM Assets. Maven packages should contain only configuration and deliberately controlled bootstrap content.

---

## ADR-004 — Rates Delivered through APIs

### Status

Accepted

### Decision

Credit-card and GIC rates will not be embedded in images or static page content.

### Rationale

Rates change independently of the page and must remain owned by the relevant system of record. EDS will retrieve them through a published service or backend-for-frontend.

## ADR — Security Scanning Strategy

SAST, software-composition analysis and secret scanning will run against source-code repositories during pull requests.

DAST will run against approved non-production EDS, AEM Publish and API endpoints after deployable runtime functionality is available.

AEM Author will not be subjected to unrestricted automated DAST. Authenticated Author testing will use approved accounts, controlled scope and a dedicated non-production environment.

## ADR-005 — RepoInit for DAM Foundation

### Status

Accepted

### Decision

Use RepoInit to create the RBC metadata namespace, DAM folder hierarchy,
security groups and folder permissions.

### Rationale

RepoInit provides repeatable, version-controlled and environment-consistent
repository initialization. It avoids relying on manual environment setup.

---

## ADR-006 — Scoped DAM Permissions

### Status

Accepted

### Decision

Apply custom permissions only under:

`/content/dam/rbc-eds-demo`

The custom RBC groups inherit standard AEM Assets access through `dam-users`.

### Rationale

This follows least-privilege principles while retaining the standard AEM Assets
authoring experience.

---

## ADR-007 — Author-First DAM Configuration

### Status

Accepted

### Decision

Deploy DAM authoring groups, folders and governance configuration to AEM Author.
Approved assets will be published to AEM Publish through AEM publication rather
than being committed as Maven content.

### Rationale

Asset ingestion, metadata management, review and approval are Author
responsibilities. Publish should receive approved assets and only the runtime
configuration required for delivery.