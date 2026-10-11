# Anchor Browser plugins

Cloud browsers for AI agents, as three MCP plugins. Sign in on first use.

| Plugin | URL |
| --- | --- |
| `anchor` | `https://api.anchorbrowser.io/v1/mcp` |
| `anchor-browser` | `https://api.anchorbrowser.io/v1/mcp/browser` |
| `anchor-actions` | `https://api.anchorbrowser.io/v1/mcp/actions/${SITE_DOMAIN}` |

`anchor` is the one to start with: web tasks, verified site actions, saved automations, managed logins with MFA, and browser sessions. `anchor-browser` is step-by-step control of a live browser.

`anchor-actions` asks for `SITE_DOMAIN`, a bare domain such as `amazon.com`.

## Cursor

Install from the Cursor marketplace, or add this repository as a plugin marketplace.

## Claude Code

```bash
claude plugin marketplace add anchorbrowser/anchor-mcp-plugin
claude plugin install anchor@anchorbrowser
```

The same install names work for `anchor-browser` and `anchor-actions`. Claude Code asks for the site domain when `anchor-actions` is enabled.

## Grok

```bash
grok mcp add --transport http anchor https://api.anchorbrowser.io/v1/mcp
grok mcp add --transport http anchor-browser https://api.anchorbrowser.io/v1/mcp/browser
grok mcp add --transport http anchor-actions https://api.anchorbrowser.io/v1/mcp/actions/amazon.com
```

`.grok/config.toml` has the two servers with fixed URLs. Actions stay out of that file because the domain is part of the URL.
