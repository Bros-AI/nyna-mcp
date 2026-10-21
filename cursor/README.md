# Nyna in Cursor

**One click:** [Add Nyna to Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=nyna&config=eyJ1cmwiOiJodHRwczovL255bmEuYWkvbWNwIn0=)

The deeplink is `cursor://anysphere.cursor-deeplink/mcp/install?name=nyna&config=<base64>` where `<base64>` is the base64 of the server entry `{"url":"https://nyna.ai/mcp"}`:

```text
cursor://anysphere.cursor-deeplink/mcp/install?name=nyna&config=eyJ1cmwiOiJodHRwczovL255bmEuYWkvbWNwIn0=
```

**By hand:** copy [`mcp.json`](./mcp.json) to `~/.cursor/mcp.json` (every project) or `.cursor/mcp.json` (one project), then Settings → MCP → turn **nyna** on. The first signed-in tool opens nyna.ai in the browser to connect your account (OAuth 2.1; no API key).

Markdown button for READMEs and cursor.directory:

```markdown
[![Add Nyna to Cursor](https://img.shields.io/badge/Add_to-Cursor-000000)](cursor://anysphere.cursor-deeplink/mcp/install?name=nyna&config=eyJ1cmwiOiJodHRwczovL255bmEuYWkvbWNwIn0=)
```
