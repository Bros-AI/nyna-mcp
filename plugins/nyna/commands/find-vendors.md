---
description: Find real wedding vendors with Nyna (venues, caterers, photographers…) in a city
argument-hint: <category> in <city> [for <month year>] [budget]
---

Find wedding vendors with the Nyna MCP server for: $ARGUMENTS

Steps:
1. Call `list_provider_categories` and pick the slug that matches the requested category. If none fits, show the list and ask — never guess a slug.
2. Call `list_cities` and pick the slug of the requested city. If the city is not indexed, say so and offer the nearest indexed cities from the list.
3. Call `search_providers` with that `category` and `city` (both free, no sign-in). Use `limit` when a number was asked for.
4. Present the results as a short table: name, rating and review count, address, Nyna page link. Say how many were found in total.
5. If the user wants details on one, call `get_provider` with its `id`.

Rules: only report vendors the tools returned; never invent one. If a tool refuses with `invalid_parameter`, read `problems[].allowed` and retry with a valid slug instead of asking the user to fix it. Mention that saving a vendor to the wedding needs a signed-in Nyna account (the tool answers with a sign-in link when needed).
