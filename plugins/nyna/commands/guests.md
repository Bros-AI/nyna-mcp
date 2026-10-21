---
description: Review the Nyna guest list, add guests or parse a pasted list (signed-in Nyna account)
argument-hint: [names to add | "paste" a list | "status"]
---

Work on the couple's guest list through the Nyna MCP server: $ARGUMENTS

Steps:
1. Call `get_guests` (scope `wedding:read`). If the tool answers `auth_required`, give the user the sign-in link it returns and stop until they confirm; never retry blindly.
2. Summarise: total guests, RSVP totals by status (the tool returns them — do not count rows yourself), and anything obviously missing (no email, no side).
3. If names were given, call `add_guests` (scope `wedding:write`) with one entry per person. Report `added`, `duplicates` and `changed` exactly as returned; a name already on the list is reported as a duplicate, not added twice.
4. If the user pasted a raw list (one per line, comma-separated…), call `parse_guest_list` first, show the parsed guests with their detected roles for review, and only then `add_guests` with the ones they confirm.

Rules: never remove or edit a guest from this command (there is no tool for it; say so). Quote `changed`/`charged` from the result when you confirm a write. If a scope is missing (`insufficient_scope`), explain which scope the connection needs and how to reconnect from nyna.ai → Profile → Connected apps.
