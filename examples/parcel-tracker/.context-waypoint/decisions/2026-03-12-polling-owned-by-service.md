# Decision: polling is owned by the server service

- **Date:** 2026-03-12
- **Status:** accepted
- **Tags:** delivery-status, security, architecture
- **Supersedes / superseded by:** None

## Context

Parcel status must refresh while preserving provider access controls and a consistent view across browser sessions.

## Decision

The server-side delivery service polls the provider and persists normalized status updates. Browser clients read status from the application API.

## Rationale

This keeps provider access in one controlled location and allows duplicate provider events to be handled consistently.

## Alternatives considered

Direct browser polling was rejected because it would expose provider access patterns and make rate limiting and duplicate handling inconsistent.

## Consequences

The delivery service needs idempotency checks and focused verification for repeated events.
