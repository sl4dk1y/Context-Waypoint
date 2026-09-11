# Operating model

## Progressive retrieval

Context Waypoint is a project memory, not an automatic prompt dump. Begin with `CURRENT.md` and the essential constraints. Add only task-relevant accepted decisions and the handoff linked from current state.

Load a proposed decision only when the task explicitly concerns it, `CURRENT.md` identifies it as active/relevant, the active handoff identifies it as relevant, or resolving it is part of the work. Read sessions, archives, rejected decisions, and superseded decisions only to answer a specific unresolved question. Stop as soon as the needed context is established.

This preserves token budget for the actual task and prevents historical detail from obscuring the current objective.

## Evidence during initialization

When initializing an existing project, derive durable context only from verifiable sources: explicit current user instructions, repository rules, approved specifications, current documentation, verified source code, verified tests, existing authoritative records, or project context explicitly supplied by the user.

Do not invent historical rationale, rejected alternatives, user intent, formal acceptance, dates, or authorship. Seeing that verified code uses a technology can support “the verified current implementation uses it”; it does not establish why it was chosen. When rationale, status, or history is unknown, omit it or record only the verified state, mark uncertainty where useful, and ask when the gap materially affects the work.

## Existing-project bootstrap

For an existing project with suitable documentation, use a selective documentation bootstrap:

1. Determine the project root and inspect repository rules.
2. Discover likely high-value sources that actually exist: a primary overview, current status, approved specifications, architecture or decision records, plans, policies, operational guidance, or existing authoritative project records.
3. Read the entry points and follow only references relevant to current state, milestones, durable constraints, explicit decisions, or unresolved work.
4. Extract concise, verified continuity into `.context-waypoint/`; inspect code, tests, configuration, or further documentation only to verify an implementation-sensitive claim or resolve an important discrepancy.

Do not read every Markdown file or perform broad repository archaeology merely to fill the store. Documentation is a high-value starting point, not automatic current truth; resolve material discrepancies using the source hierarchy below.

An initial store may contain only `CURRENT.md` and `CONSTRAINTS.md`, perhaps a small number of explicitly supported decisions, an initialization session that records material bootstrap evidence or discrepancies, or one active handoff. Empty record directories are valid. Do not reconstruct historical handoffs, synthetic session histories, or an archive from existing documents merely because those directories exist.

## Reference, don't duplicate

Context Waypoint compresses project knowledge; it is not a second copy of project documentation. For a large policy, specification, architecture description, or operational guide, record only the durable fact that affects future work and a simple source path or link when useful. Keep the full detail in the authoritative document.

For example, a constraint can state “Production deployment requires explicit user authorization” and point to the repository policy instead of reproducing that policy. Keep `CONSTRAINTS.md` small enough for normal minimal-context loading.

## Store project state, not agent/tool state

Store durable project conclusions, not temporary inspection conditions such as which model, index, MCP connection, or navigation tool was available. Session records may include useful concise agent/environment provenance, but incidental tool output or operational status does not belong in durable project context without a project-specific reason.

## Staleness and conflicts

Waypoint records are evidence, not unquestionable truth. Resolve conflicts using this order:

1. Explicit current user instructions.
2. Current repository rules and policies.
3. Approved current specifications.
4. Verified current source code and tests.
5. Current accepted Waypoint records.
6. Historical, rejected, or superseded Waypoint records.

When sources conflict, do not silently choose the convenient one or rewrite history to hide the conflict. State the conflict, verify the higher-priority source where possible, follow it, and update or supersede durable context only after the new state is established.

## Privacy and boundaries

Assume the directory can be committed and copied. Never record passwords, tokens, private keys, cookies, credentials, private connection strings, secret endpoints, raw `.env` contents, sensitive logs, personal confidential data, or unrelated private project information. Keep only the non-sensitive conclusion and, if necessary, a pointer to an approved secure location without revealing it.

Context Waypoint is standalone and can coexist with other workflow, navigation, or development tools. Keep its scope to durable project continuity.
