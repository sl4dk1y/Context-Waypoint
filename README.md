# Context Waypoint

**Portable project continuity for AI coding agents.**

Context Waypoint is a small, Git-friendly convention for preserving the project knowledge that should survive an AI session: current work, constraints, decisions, concise session summaries, and handoffs. It uses Markdown and ordinary directories, so a repository can carry its own continuity context without a database, daemon, cloud service, or model-specific history.

It is designed around one rule: **store broadly, load narrowly.** Keep useful history, but load only the small amount needed for the task at hand.

## What it solves

Long-running AI-assisted work often loses decisions, constraints, unfinished work, and the rationale behind an earlier choice. Replaying a full chat transcript is noisy, expensive, and often less useful than a concise record of the result.

Context Waypoint gives future agents a durable starting point without attempting to preserve every conversation. It is not a chat archive, code index, memory database, workflow orchestrator, or automatic summarization service. Do not put chain-of-thought, source-code inventories, raw logs, secrets, or credentials in it.

## Storage model

Project-specific Context Waypoint data always lives at `<project-root>/.context-waypoint/`. For a Git project, the project root is normally the directory containing `.git`, alongside source directories, tests, and the project README:

```text
some-project/
├── .git/
├── .context-waypoint/
│   ├── CURRENT.md
│   ├── CONSTRAINTS.md
│   ├── decisions/
│   ├── handoffs/
│   ├── sessions/
│   └── archive/
├── src/
├── tests/
└── README.md
```

`CURRENT.md` is deliberately not a changelog. It answers what the project is trying to achieve, where work stands, what is active or blocked, and what should happen next. It links to an active handoff rather than reproducing it.

Decision records are the only source of truth for decisions. There is no aggregate `DECISIONS.md` index to become stale. Use filenames such as `2026-03-18-choose-storage.md`, and mark obsolete records `superseded` or `rejected`.

The packaged [schema reference](skills/context-waypoint/references/schema.md) defines record responsibilities. The [operating model](skills/context-waypoint/references/operating-model.md) covers retrieval, evidence, conflicts, and privacy.

## Installation and initialization

Context Waypoint follows an Agent Skills-style portable structure. Install the reusable skill once; each project then gets its own isolated `.context-waypoint/` directory. The recommended shared installation example is:

```sh
mkdir -p ~/.agents/skills
cp -R /path/to/context-waypoint/skills/context-waypoint ~/.agents/skills/context-waypoint
```

The installed skill at `~/.agents/skills/context-waypoint/` is self-contained: its templates and references live beside `SKILL.md`. From the root of an unrelated target project, initialize that project's store from the installed skill:

```sh
cp -R ~/.agents/skills/context-waypoint/templates/.context-waypoint .context-waypoint
```

Then replace the placeholders in `CURRENT.md` and `CONSTRAINTS.md`. Add a decision, session, or handoff only when it gives a future agent material information it would otherwise need to rediscover. Record skeletons are in `~/.agents/skills/context-waypoint/templates/records/`.

Do not create `.context-waypoint/` in the installed skill directory, at `~/.context-waypoint/`, beside the project, or as a shared store for multiple projects. If the project root is ambiguous, establish it or ask before initializing rather than guessing across unrelated directories.

Individual agent environments may use different skill-discovery locations. Follow that environment's documentation if it does not discover `~/.agents/skills/`. This project does not claim compatibility with untested agent environments and does not modify global configuration for you.

For a concrete, fictional project, see [the parcel tracker example](examples/parcel-tracker).

## Retrieval discipline

Never start by reading every file under `.context-waypoint/`.

1. **Minimal:** read `CURRENT.md` and the essential constraints.
2. **Relevant:** additionally read accepted decision records related to the task and the active/relevant handoff. Read a proposed decision only when the task explicitly concerns it, current state or the handoff identifies it as relevant, or resolving it is the work.
3. **Deep:** inspect selected sessions, rejected or superseded decisions, historical handoffs, or archive material only when a current question cannot be resolved from the smaller set.

This keeps routine tasks small while retaining evidence for investigations and long-running work.

## Stale context and public safety

Waypoint records are evidence, not authority over current reality. When sources conflict, follow current user instructions, current repository rules, approved specifications, and verified source/tests before accepted current Waypoint records; treat historical, rejected, and superseded records as lower-priority context. Surface conflicts rather than silently choosing stale history, and update durable records only after the new state is established.

During initialization in an existing project, record only verifiable current facts and explicitly supplied project context. Do not invent historical rationale, rejected alternatives, intent, acceptance status, dates, or authorship from source code alone.

Treat `.context-waypoint/` as potentially public and committed. Never store passwords, API tokens, private keys, cookies, credentials, private connection strings, secret URLs, raw `.env` contents, sensitive logs, confidential personal information, or unrelated private project information.

`.context-waypoint/` is designed to be Git-friendly and may normally be tracked with its project so continuity travels with the repository. It is not automatically added to `.gitignore`, and Context Waypoint never performs Git writes. The user and repository policy decide what is committed.

## Project status

v0.1 is a portable Markdown convention, a self-contained Agent Skill, reusable templates, and a neutral example. It intentionally has no database, embeddings, MCP server, daemon, web UI, telemetry, network service, CLI, or runtime dependency. It is standalone and can coexist with other workflow, navigation, or development tools.

## License

[MIT](LICENSE)
