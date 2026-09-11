# Security policy

## Scope

Context Waypoint v0.1 is a Markdown-only Agent Skill and project-continuity convention. It has no executable runtime, CLI, network service, dependencies, daemon, MCP server, telemetry, or cloud component.

Security-relevant reports may include guidance or behavior that could expose secrets or confidential data in `.context-waypoint/`, mix context from unrelated projects, or create unsafe filesystem/path behavior. If future versions introduce executable tooling or dependencies, dependency, supply-chain, and code-execution issues may also be security-relevant.

Not every privacy mistake or documentation error is a security vulnerability. Use normal Issues for non-sensitive bugs, feature requests, usability problems, and ordinary documentation corrections.

## Reporting a vulnerability

When GitHub private vulnerability reporting or repository security advisories are available, use that channel for sensitive details. Do not publish sensitive vulnerability details in a public Issue.

Please provide a concise description, affected files or guidance, potential impact, and safe reproduction information where possible. No response-time commitment is currently made.

## Supported versions

There is no tagged stable release yet. During this pre-release stage, security fixes are expected to target the latest version on the default branch.

## Project data safety

`.context-waypoint/` may be tracked by Git and may be public. Never store passwords, tokens, private keys, cookies, credentials, private connection strings, raw environment secrets, sensitive logs, confidential information, or unrelated private project context there. Keep each project's context at that project's root; do not use a shared multi-project store.

Current user instructions and repository policy remain authoritative. See the [README](README.md#stale-context-and-public-safety) and the skill's [operating model](skills/context-waypoint/references/operating-model.md#privacy-and-boundaries) for the full privacy and project-isolation guidance.
