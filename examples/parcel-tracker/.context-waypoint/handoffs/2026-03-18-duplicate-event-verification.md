# Handoff: verify duplicate provider events

- **Date:** 2026-03-18
- **Status:** active

## Objective

Demonstrate that a repeated provider event cannot create a second visible status transition.

## Complete

The service accepts normalized provider updates and persists one status transition per unique event.

## Incomplete and blockers

An automated fixture for the same event delivered twice has not yet been added. There is no known implementation blocker.

## Relevant context

- [Current state](../CURRENT.md)
- [Server-owned polling decision](../decisions/2026-03-12-polling-owned-by-service.md)
- [Provider access constraint](../CONSTRAINTS.md)

## Required verification

Run the focused duplicate-event check and the delivery-status test suite. Confirm the second event causes no additional stored transition.

## Recommended next action

Create the duplicate-event fixture, run the relevant checks, then either mark this handoff resolved or record the discovered blocker.
