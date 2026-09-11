# Project constraints

## Provider access stays server-side

- **Rule:** Browser clients must not call the delivery provider directly.
- **Why:** Provider authentication and rate limits must remain under server control.
- **Change control:** Requires an approved security review and updated architecture decision.
