# Nyna for ChatGPT and Codex (draft plugin)

Two ways to use Nyna from OpenAI products; only the first works today without a review.

## 1. Custom connector (works now)

ChatGPT → Settings → Connectors → **Create** (developer mode must be on for the account) → name `Nyna`, MCP server URL `https://nyna.ai/mcp`, authentication **OAuth** (ChatGPT registers itself through dynamic client registration; nothing to paste). Pick the connector in a new chat (Tools → Nyna).

## 2. Plugin / Apps directory (draft, owner to submit)

The layout follows the examples in [openai/plugins](https://github.com/openai/plugins) (`plugins/<name>/.codex-plugin/plugin.json` + `.mcp.json`, e.g. `notion`, `linear`):

- [`.codex-plugin/plugin.json`](./.codex-plugin/plugin.json): the manifest. The `_owner_todo` block lists what must be filled before submitting and is not part of the schema; delete it then.
- [`.mcp.json`](./.mcp.json): the remote server, `type: http`, with `oauth_resource` set to the protected-resource identifier (`https://nyna.ai/mcp`, as `/.well-known/oauth-protected-resource/mcp` declares).
- `assets/`: copy `distribution/assets/icon-512.png` and the three screenshots here (paths referenced by the manifest).
- `.app.json`: created after the app exists in the OpenAI developer console (`asdk_app_…` id).

Submission is through the ChatGPT apps developer flow (developers.openai.com → Apps SDK → submit); the review needs the demo account described in `distribution/COPY.md` and the test cases there.
