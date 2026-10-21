---
description: Draft and save the wedding-day run sheet with Nyna (signed-in Nyna account)
argument-hint: [ceremony time, venue constraints, "save"]
---

Build the wedding-day schedule through the Nyna MCP server: $ARGUMENTS

Steps:
1. Call `get_wedding` and `get_day_of_timeline` (scope `wedding:read`) to learn the date, venue, ceremony type, guest count and what is already on the run sheet. On `auth_required`, hand the user the sign-in link and stop.
2. Call `suggest_day_schedule` (sign-in required; it says in its description whether it spends credits — tell the user before calling if it does). It returns a 10–15 event timeline in 24h time for review; nothing is written yet.
3. Show the proposed timeline as a table (time, event, who, notes) and ask what to change. Apply the changes in the text, keep every time as `HH:MM` and in order.
4. Only when the user says "save": call `set_run_sheet` (scope `wedding:write`) with the reviewed timeline. It replaces the whole sheet, so say so first. Report `changed` and `charged` from the result.

Rules: an out-of-order sheet is refused by the tool rather than stored; fix the order before retrying. Never save without an explicit go-ahead. Mention that the live run sheet is at https://nyna.ai/wedding/day-of.
