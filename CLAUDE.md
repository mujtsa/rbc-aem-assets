@AGENTS.md

# Claude Code Instructions

## Project Context

This repository is an AEM as a Cloud Service Maven project focused on AEM Assets.

Use the existing Maven module structure and the architecture documented in `AGENTS.md`.

This repository is separate from:

- the AEM Edge Delivery Services website repository
- the Adobe Developer App Builder repository
- author-managed DAM asset binaries and content

## Adobe Skills

Use the installed official Adobe AEM as a Cloud Service skills whenever applicable.

Prefer the relevant installed skill for:

- AEM Cloud Service best practices
- Maven and content-package structure
- OSGi services and configurations
- RepoInit permissions
- AEM workflows
- Dispatcher configuration
- code assessment
- local SDK development
- RDE and Cloud Manager deployment guidance

Do not apply AEM Edge Delivery Services block-development conventions to this repository.

## Token Efficiency

Minimize token usage while preserving correctness.

- Keep responses concise and action-oriented.
- Do not restate the request or repeat repository context already available in `AGENTS.md`.
- Read only files directly relevant to the task.
- Prefer targeted searches over broad repository scans.
- Do not repeatedly read the same files unless they changed.
- Load only the Adobe skill required for the current task.
- Do not load every installed skill pre-emptively.
- Avoid lengthy explanations unless explicitly requested.
- Present a short implementation plan only for multi-file or architectural changes.
- For simple changes, implement directly and provide a brief completion summary.
- Show only the relevant code diff or changed sections rather than entire files.
- Avoid generating optional documentation, tests, examples, or abstractions unless required.
- Reuse existing utilities, patterns, and configurations instead of creating parallel implementations.
- Run the narrowest relevant Maven command first; run a full build only when needed.
- Ask before performing broad codebase analysis, large refactors, or generating many files.
- When blocked, report the exact blocker and the smallest next action.

## Architecture Rules

- Keep immutable application code and mutable repository content in the appropriate Maven modules.
- Put Java and OSGi implementation code in `core`.
- Put component, workflow, dialog, and application definitions under `ui.apps` when applicable.
- Put OSGi configurations and RepoInit scripts in `ui.config`.
- Put controlled repository content, metadata schemas, workflow models, tags, and folder configuration in `ui.content` when appropriate.
- Use `all` as the aggregate deployable package.
- Keep Dispatcher configuration in the `dispatcher` module.
- Do not commit normal business asset binaries to the Maven repository.
- Upload and govern normal assets through AEM Assets.
- Use Maven packages only for deliberately controlled sample or bootstrap content.

## AEM Assets Scope

Initial implementation priorities are:

1. Create or bootstrap `/content/dam/rbc-eds-demo`.
2. Configure access using RepoInit.
3. Create an RBC-specific metadata schema.
4. Apply the metadata schema to the appropriate DAM folders.
5. Configure asset review and approval workflows where required.
6. Validate asset publishing from local Author to local Publish.
7. Prepare configuration for later AEM as a Cloud Service deployment.

## Security and Permissions

- Use RepoInit for repository users, service users, groups, and ACLs.
- Follow least-privilege access.
- Do not hardcode passwords, tokens, API keys, or environment-specific credentials.
- Do not use administrative sessions in custom Java code.
- Use service users and Sling Resource Resolver mappings where repository access is needed.
- Do not log credentials, sensitive metadata, or private asset information.
- Review upload validation, file types, workflow permissions, and public asset exposure.

## Development Standards

Before implementing changes:

1. Inspect the root `pom.xml` and affected Maven modules.
2. Inspect existing project conventions and package filters.
3. Load and follow the relevant installed Adobe skill.
4. Present the approach before making major structural changes.
5. Implement the smallest maintainable change.
6. Preserve Cloud Service compatibility.
7. Run relevant Maven compilation, unit tests, and validation checks.
8. Report any manual AEM authoring or configuration steps.

Use Java APIs supported by AEM as a Cloud Service and the project’s configured SDK API dependency.

Do not introduce deprecated APIs, unsupported repository writes, or customizations that depend on modifying immutable runtime areas.

## Build and Local Installation

Use the repository root for Maven commands.

Standard build:

```powershell
mvn clean install
```

Install the aggregate package on local Author:

```powershell
mvn clean install -PautoInstallPackage "-Daem.host=localhost" "-Daem.port=4502" "-Dvault.user=admin" "-Dvault.password=admin"
```

Do not install packages on Author or Publish unless explicitly requested.

Do not publish assets, deploy to Cloud Manager, merge branches, or modify credentials unless explicitly requested.

## Dispatcher

- Preserve the generated AEM Cloud Service Dispatcher structure.
- Validate changes using the Dispatcher SDK tools when available.
- Do not expose repository paths or APIs without an explicit requirement.
- Apply allowlists, caching rules, headers, and invalidation rules deliberately.
- Remember that Dynamic Media or dedicated asset-delivery services may bypass the project Dispatcher.

## Testing

Where applicable, run:

- Maven compilation
- unit tests
- content-package validation
- OSGi configuration validation
- RepoInit validation
- Dispatcher validation
- local Author package installation
- local Author-to-Publish asset publication testing

Do not claim a test passed unless it was actually executed successfully.

## Completion Report

After completing a task, summarize:

- files created or changed
- Maven modules affected
- commands and tests executed
- assumptions made
- local installation steps
- manual AEM configuration or authoring steps
- Cloud Manager or deployment considerations
- known limitations or unresolved issues

## Documentation

Maintain these files as implementation progresses:

- `docs/aem-assets-implementation-guide.md`
- `docs/implementation-log.md`
- `docs/architecture-decisions.md`
- `docs/asset-inventory.md`

After a successfully validated change:

1. Append a concise dated entry to `implementation-log.md`.
2. Update the implementation guide only when a capability or validated procedure changes.
3. Add an architecture decision only for a meaningful technical choice.
4. Update the asset inventory when assets, DAM paths, metadata, or source systems change.
5. Do not include passwords, credentials, private URLs, personal data, or unnecessary terminal output.
6. Do not rewrite unchanged documentation.
7. Keep client-facing documentation professional and concise.