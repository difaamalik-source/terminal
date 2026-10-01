# terminal

Claude Code workspace wired up to GoMining:

- **GoMining AI Skills**: 16 knowledge skills in `.claude/skills/` (platform, miners, VIP, token,
  tokenomics, wallet, Simple Earn, Instant Funds, card, payments, cashback, travel, promos,
  academy, avatars, investment guide). Claude loads them automatically in this repo.
  Source: [docs](https://docs.gomining.com/en/product/ai/skills) ·
  [repo](https://github.com/gomining-ai/gomining-agent-skills).
- **GoMining MCP Server**: declared in `.mcp.json` as `gomining`, giving Claude live access to
  your GoMining account (balances, miners, rewards, Simple Earn positions, card activity,
  market prices). Docs: <https://docs.gomining.com/en/product/ai/mcp-server>.

## MCP server setup

Server URL: `https://mcp.gomining.com/mcp` (already in `.mcp.json`).

1. Start `claude` in this repo.
2. Run `/mcp`, select **gomining** and sign in to GoMining when prompted.
   Grant **read** access unless you want Claude to act on your account.

If GoMining gives you an API key instead of a sign-in flow, keep the key out of git and reference it
from an env var:

```json
"gomining": {
  "type": "http",
  "url": "https://mcp.gomining.com/mcp",
  "headers": { "Authorization": "Bearer ${GOMINING_API_KEY}" }
}
```

Check:

```bash
claude mcp get gomining
```

### Claude Code on the web

Cloud sessions block unknown hosts by default. Add `mcp.gomining.com` (or `*.gomining.com`) to the
environment's allowed domains (environment menu → Edit → Network access), otherwise the MCP
server can't be reached.

### Claude desktop / claude.ai

Settings → Connectors → Add custom connector, paste `https://mcp.gomining.com/mcp`.
