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

Proposed

### Decision

Use RepoInit to create AEM groups and manage DAM permissions.

### Rationale

RepoInit provides repeatable, version-controlled and environment-consistent authorization configuration.

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