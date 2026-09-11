# Current state

## Objective

Finish the first internal release of delivery-status polling for Parcel Tracker.

## Status

Polling is implemented against the provider sandbox; the release remains blocked on validating duplicate-event handling.

## Active work

The team is adding focused verification around repeated provider updates.

## Blockers

No sandbox examples currently cover an event arriving twice after a retry.

## Next action

Add a focused duplicate-event fixture, verify the stored status stays unchanged after the second event, and update the active handoff.

## Relevant decisions

[Server-owned polling](decisions/2026-03-12-polling-owned-by-service.md)

## Active handoff

[Duplicate-event verification](handoffs/2026-03-18-duplicate-event-verification.md)
