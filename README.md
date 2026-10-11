# Anchor Browser plugins

Cloud browsers for AI agents, as four MCP plugins. Sign in on first use.

| Plugin | URL |
| --- | --- |
| `anchor` | `https://api.anchorbrowser.io/v1/mcp` |
| `anchor-all` | `https://api.anchorbrowser.io/v1/mcp/all` |
| `anchor-browser` | `https://api.anchorbrowser.io/v1/mcp/browser` |
| `anchor-actions` | `https://api.anchorbrowser.io/v1/mcp/actions/${SITE_DOMAIN}` |

Install `anchor` or `anchor-all`, not both. Their tool names overlap. `anchor` is the one to start with. `anchor-all` is every REST capability as its own tool.

`anchor-actions` asks for `SITE_DOMAIN`, a bare domain such as `amazon.com`.

## Cursor

Install from the Cursor marketplace, or add this repository as a plugin marketplace.

## Claude Code

```bash
claude plugin marketplace add anchorbrowser/anchor-mcp-plugin
claude plugin install anchor@anchorbrowser
```

For actions, set `SITE_DOMAIN` to the bare domain before the first connection. The same install names work for `anchor-all`, `anchor-browser`, and `anchor-actions`.

## Grok

```bash
grok mcp add --transport http anchor https://api.anchorbrowser.io/v1/mcp
grok mcp add --transport http anchor-all https://api.anchorbrowser.io/v1/mcp/all
grok mcp add --transport http anchor-browser https://api.anchorbrowser.io/v1/mcp/browser
grok mcp add --transport http anchor-actions https://api.anchorbrowser.io/v1/mcp/actions/amazon.com
```

`.grok/config.toml` has the three servers with fixed URLs. Actions stay out of that file because the domain is part of the URL.
