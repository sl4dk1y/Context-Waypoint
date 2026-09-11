# Operating model

## Progressive retrieval

Context Waypoint is a project memory, not an automatic prompt dump. Begin with `CURRENT.md` and the essential constraints. Add only task-relevant accepted decisions and the handoff linked from current state.

Load a proposed decision only when the task explicitly concerns it, `CURRENT.md` identifies it as active/relevant, the active handoff identifies it as relevant, or resolving it is part of the work. Read sessions, archives, rejected decisions, and superseded decisions only to answer a specific unresolved question. Stop as soon as the needed context is established.

This preserves token budget for the actual task and prevents historical detail from obscuring the current objective.

## Evidence during initialization

When initializing an existing project, derive durable context only from verifiable sources: explicit current user instructions, repository rules, approved specifications, current documentation, verified source code, verified tests, existing authoritative records, or project context explicitly supplied by the user.

Do not invent historical rationale, rejected alternatives, user intent, formal acceptance, dates, or authorship. Seeing that verified code uses a technology can support “the verified current implementation uses it”; it does not establish why it was chosen. When rationale, status, or history is unknown, omit it or record only the verified state, mark uncertainty where useful, and ask when the gap materially affects the work.

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
