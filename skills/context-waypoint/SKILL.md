---
name: context-waypoint
description: Preserve concise, portable project continuity across AI coding sessions using project-local Markdown records.
---

# Context Waypoint

Use Context Waypoint to preserve durable project knowledge across interrupted work, agents, and models. It stores conclusions and evidence, not chat transcripts, private reasoning, code indexes, or secrets.

## When to use it

Use it when a repository has `.context-waypoint/` or when the user asks to retain project state, decisions, constraints, a session summary, or a handoff. Initialize it for a long-running project when durable continuity would avoid repeated explanation or incorrect decisions.

Do not use it for temporary scratch notes, exhaustive code navigation, full conversation history, raw logs, credentials, or information that a future agent can cheaply rediscover.

## Initialize

This installed skill is self-contained at `~/.agents/skills/context-waypoint/`; it is reusable tooling, not project data. Each project's continuity data lives only at `<project-root>/.context-waypoint/`. For a Git repository, use the directory containing `.git` as the project root; otherwise use the project directory the user has identified. If the root is ambiguous, establish it or ask rather than guessing across unrelated directories.

From the current project root, copy `templates/.context-waypoint` from the installed skill directory into `.context-waypoint/`. Do not create it in the installed skill directory, at `~/.context-waypoint/`, beside the project, or in a shared multi-project store. Fill in `CURRENT.md` and `CONSTRAINTS.md`; create records from `templates/records` only when needed. Keep the format as plain Markdown and do not add a database, daemon, embedding service, or agent-specific runtime.

The directory is Git-friendly and may normally be tracked with the project. Do not add it to `.gitignore` automatically or perform Git writes; the user and repository policy decide what is committed.

When initializing an existing project, record only verifiable current facts and context explicitly supplied by the user. Do not infer historical rationale, rejected alternatives, acceptance status, dates, authorship, or user intent from current code alone. If a material fact is uncertain, record the uncertainty or ask; prefer omission to false certainty.

## Read narrowly

Never read the entire directory by default.

1. Read `CURRENT.md` and essential constraints.
2. Read accepted decision records relevant to the task and any active/relevant handoff. Read a proposed decision only when the task concerns it, `CURRENT.md` or the handoff identifies it as relevant, or resolving it is the work.
3. Read selected sessions, archive material, rejected decisions, or superseded decisions only to resolve a specific remaining question.

Stop when the task has enough context. This protects the token budget and keeps old details from obscuring current work.

## Update the right record

- Rewrite and prune `CURRENT.md` when the objective, current state, blockers, next action, active decision, or active handoff changes. It is not a changelog.
- Add a constraint only when it is a durable guardrail, not a temporary TODO.
- Add one decision record for a material proposed, accepted, rejected, or superseded choice. Record rationale and alternatives only when actually known; link a replacement when applicable.
- Write a session summary after meaningful work: conclusions, completed work, verification, unresolved issues, and follow-up. Never include private reasoning.
- Write a handoff before pausing materially unfinished work. `CURRENT.md` should link to the active handoff rather than duplicate it. Clear that link when it is no longer active.
- Move cold historical records to `archive/` rather than loading them routinely.

Use this storage test: record something only if forgetting it would materially increase the chance of a future wrong decision or repeated work.

## Staleness and safety

Waypoint records are evidence, not authority over current reality. Resolve conflicts in this order: current user instruction, current repository rules, approved specification, verified code/tests, accepted current records, then historical, rejected, or superseded records. Surface conflicts explicitly; do not silently select stale history or rewrite it to hide an unresolved conflict. Update durable context only once the new state is established.

Assume `.context-waypoint/` may be public. Never store passwords, API tokens, private keys, cookies, credentials, private connection strings, secret URLs, raw `.env` contents, confidential personal information, unrelated private project information, or sensitive logs.

For concise field and lifecycle details, read `references/schema.md`. For fuller retrieval, evidence, conflict, and privacy guidance, read `references/operating-model.md`.
