# Nyna in VS Code (GitHub Copilot agent mode)

1. Copy [`mcp.json`](./mcp.json) to `.vscode/mcp.json` in your workspace (or add the `nyna` entry to the `servers` map of the one you have). For every workspace: **MCP: Open User Configuration** and paste the same entry there.
2. In the file, click **Start** above the server — or run **MCP: List Servers** from the command palette and start `nyna`. VS Code opens nyna.ai once for the OAuth sign-in (dynamic client registration; nothing to paste back).
3. Open Copilot Chat, switch to **Agent** mode, click the tools icon and tick **nyna**. Ask: "Find me 5 photographers in Lyon for July 2027".

Install link for docs (`vscode:` and `vscode-insiders:` URL handlers, the server config URL-encoded):

```text
vscode:mcp/install?%7B%22name%22%3A%22nyna%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fnyna.ai%2Fmcp%22%7D
```

Markdown badge:

```markdown
[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_Nyna-0098FF?logo=visualstudiocode)](vscode:mcp/install?%7B%22name%22%3A%22nyna%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fnyna.ai%2Fmcp%22%7D)
```

VS Code 1.102+ supports remote HTTP MCP servers with OAuth; older builds need `"type": "sse"` servers or a `mcp-remote` bridge, which Nyna does not provide — update VS Code instead.
