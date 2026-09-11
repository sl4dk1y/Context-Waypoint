# Context Waypoint schema

The schema is intentionally small. A record belongs in one place only; link to a record rather than copying its contents.

## `CURRENT.md`: hot state

Keep this concise enough to read at the start of ordinary tasks. Replace, prune, or rewrite it as work changes; do not append a running history. It contains the current objective, milestone/status, active work, blockers, next action, task-relevant decision links, and a relative link to an active handoff when one exists. The objective is normally the current working task, investigation, milestone work, readiness goal, or operational objective; use the verified project/milestone objective only when no narrower work is active. Its authority is current coordination, not historical evidence.

## `CONSTRAINTS.md`: durable guardrails

Use this only for durable requirements and prohibitions: compatibility promises, approval boundaries, security rules, or operational limits. State each constraint, why it exists, and how it can be changed. Add a short source path or link in the rationale when useful; do not copy a large repository policy. Do not put temporary tasks, hypotheses, or stale implementation notes here.

## `decisions/`: durable decisions

One file is one decision. Use a stable, readable filename such as `YYYY-MM-DD-short-title.md`. A decision record has a date, status, context, decision, rationale when known, alternatives when known, consequences, optional tags, and an optional relation to a replacement record.

Allowed statuses are `proposed`, `accepted`, `superseded`, and `rejected`. Only `accepted` records are normally binding. A proposed record is current context only when the task concerns it or it is linked by `CURRENT.md` or the active handoff. Rejected and superseded records are historical by default. An existing historical decision may be added only when an authoritative source explicitly supports the recorded facts and the decision remains useful; current implementation alone does not establish historical rationale or acceptance. When replacing an accepted decision, update the old record to `superseded` and link both records. Do not maintain a summary index: the individual records are authoritative.

## `sessions/`: concise historical summaries

Create a session summary only for meaningful work that is useful later, such as a substantial investigation, audit, implementation unit, milestone, verification pass, or incident analysis. It records conclusions and durable evidence, not a transcript, private reasoning, or every conversation. A summary may link to a decision or handoff, but should not duplicate it.

## `handoffs/`: unfinished-work continuation

Create a handoff only when another agent needs to continue work that is materially unfinished or deliberately paused at a non-trivial state. Describe the objective, complete and incomplete work, blockers, relevant records, high-level components, required verification, and recommended next action. `CURRENT.md` identifies the active relevant handoff. When the work is complete, clear that reference and archive the handoff if its history still matters.

## `archive/`: cold context

Move superseded sessions, decisions, or handoffs here when they are valuable for audit/history but should not appear in normal retrieval. Preserve relative links when practical and mark a moved record clearly. Archives are never default context.

## Record lifecycle

1. Update `CURRENT.md` when the current objective, status, blocker, next action, active decision, or active handoff changes.
2. Record a material proposed, accepted, rejected, or superseded choice in `decisions/` when its explicitly supported context will prevent repeated work or mistakes.
3. Use a session summary after meaningful completed work; use a handoff before pausing unfinished work.
4. Prune `CURRENT.md`; archive records that are historical but no longer relevant.

Empty `decisions/`, `handoffs/`, `sessions/`, and `archive/` directories are valid after initialization.

Before saving any record, ask: “Would forgetting this materially increase the risk of a future wrong decision or repeated work?” If not, leave it out.
