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

1. Copy the server URL from the [MCP server docs page](https://docs.gomining.com/en/product/ai/mcp-server).
2. Export it before starting Claude Code:

   ```bash
   export GOMINING_MCP_URL="<url from the docs>"
   claude
   ```

   Or replace `${GOMINING_MCP_URL}` in `.mcp.json` with the URL directly (it is not a secret).
3. In Claude Code run `/mcp`, select **gomining** and sign in to GoMining when prompted.
   Grant **read** access unless you want Claude to act on your account.

If the docs give you an API key instead of a sign-in flow, keep the key out of git and reference it
from an env var:

```json
"gomining": {
  "type": "http",
  "url": "${GOMINING_MCP_URL}",
  "headers": { "Authorization": "Bearer ${GOMINING_API_KEY}" }
}
```

Check:

```bash
claude mcp get gomining
```

### Claude Code on the web

Cloud sessions block unknown hosts by default. Add `gomining.com` and `*.gomining.com` to the
environment's allowed domains (environment menu → Edit → Network access), otherwise the MCP
server can't be reached.

### Claude desktop / claude.ai

Settings → Connectors → Add custom connector, paste the same URL.
