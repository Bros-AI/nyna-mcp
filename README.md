# Nyna MCP — the AI wedding planner, in your AI assistant

[![MCP server](https://img.shields.io/badge/MCP-nyna.ai%2Fmcp-C9A96E)](https://nyna.ai/mcp)
[![Official MCP registry](https://img.shields.io/badge/registry-io.github.Bros--AI%2Fnyna-3A3732)](https://registry.modelcontextprotocol.io/?q=nyna)
<!-- Glama badge: paste the one Glama gives you after claiming the server, e.g.
<a href="https://glama.ai/mcp/servers/<id>"><img width="380" height="200" src="https://glama.ai/mcp/servers/<id>/badge" alt="Nyna MCP server" /></a> -->
[![License: MIT](https://img.shields.io/badge/license-MIT-7A9B7E)](./LICENSE)

[Nyna](https://nyna.ai) plans weddings in a conversation: a full plan, real vendors from an indexed directory (venues, caterers, photographers…), the guest list and RSVPs, the budget, the checklist and a minute-by-minute wedding-day run sheet.

This repository holds the **client-side packaging** of Nyna's remote MCP server. There is nothing to run: the server lives at `https://nyna.ai/mcp` (Streamable HTTP, OAuth 2.1 with PKCE and dynamic client registration). The directory tools answer with no account; a couple's own wedding appears after one sign-in.

Step-by-step install for every client, with copy buttons: **https://nyna.ai/assistants**

## Claude Code

```bash
claude mcp add --transport http nyna https://nyna.ai/mcp
```

Or as a plugin (adds `/nyna:find-vendors`, `/nyna:guests` and `/nyna:day-of`):

```text
/plugin marketplace add Bros-AI/nyna-mcp
/plugin install nyna@nyna-mcp
```

## Claude (claude.ai / desktop)

Settings → Connectors → **Add custom connector** → URL `https://nyna.ai/mcp` → Connect.

## ChatGPT

Settings → Connectors → **Create** (developer mode) → name `Nyna`, URL `https://nyna.ai/mcp`. The draft Codex/ChatGPT plugin manifest is in [`chatgpt/`](./chatgpt).

## Cursor

One click: [Add Nyna to Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=nyna&config=eyJ1cmwiOiJodHRwczovL255bmEuYWkvbWNwIn0=) — or copy [`cursor/mcp.json`](./cursor/mcp.json) into `.cursor/mcp.json`.

## VS Code

Copy [`vscode/mcp.json`](./vscode/mcp.json) to `.vscode/mcp.json`, then **MCP: List Servers → Start** and tick Nyna in Copilot Chat's tools picker.

## Any other client

```json
{ "mcpServers": { "nyna": { "url": "https://nyna.ai/mcp" } } }
```

## What you can ask

- "Find me 5 photographers in Lyon for July 2027"
- "Add Marie and Pierre Dupont to my guest list"
- "Draft the schedule for my wedding day"

## Tools, cost, privacy

- Every tool description opens with its tier: `[Free]`, `[Sign-in required]`, `[Partner]` or `[Credits: N]`. Chat with Nyna is free; a wedding plan costs 5 credits and a vendor search 2; every account starts with 500 free credits.
- Scopes are granted by name (`directory:read`, `wedding:read`, `wedding:write`, `planning:run`, `partner:read`, `partner:write`); a token with `wedding:read` is refused a write.
- Every refusal carries a machine-readable `code` and `changed: false, charged: 0`. Unknown parameters are refused, never silently dropped.
- Revoke an app at any time in **Profile → Connected apps** on nyna.ai.
- Machine-readable summary: https://nyna.ai/llms.txt · technical docs: https://nyna.ai/for-agents · privacy: https://nyna.ai/privacy

## Layout

```text
.claude-plugin/marketplace.json   Claude Code marketplace (one plugin: nyna)
plugins/nyna/                     the plugin: .claude-plugin/plugin.json, .mcp.json, commands/
cursor/                           deeplink + mcp.json
vscode/                           .vscode/mcp.json
chatgpt/                          Codex / ChatGPT plugin draft (.codex-plugin/plugin.json, .mcp.json)
server.json                       (to add: the official-registry manifest from the nyna repo root)
```

Support: contact@nyna.ai · Nyna AI SAS, Paris.
