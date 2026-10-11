# Anchor for Grok Build

One plugin, two hosted MCP servers. Sign in with your Anchor account on first use; there is no API key to paste and nothing runs on your machine.

| Server | URL | What it does |
| --- | --- | --- |
| `anchor` | `https://api.anchorbrowser.io/v1/mcp` | Web tasks that get past bot detection, verified site actions, saved automations, managed logins with MFA, browser sessions with residential proxies and captcha solving, docs, and `call_endpoint_*` for the rest of the API. |
| `anchor-browser` | `https://api.anchorbrowser.io/v1/mcp/browser` | Step-by-step control of a live Anchor browser: `anchor_navigate`, `anchor_snapshot`, `anchor_click`, `anchor_type`, screenshots, network and console logs, and Playwright code generation. |

Start with `anchor` for anything that should just get done; use `anchor-browser` when the agent needs to drive the page itself. Both servers share one sign-in, and `anchor-browser` can attach to a session created on `anchor` by sending its id in an `anchor-session-id` header, so a signed-in session can be handed back and forth.

## Install

```bash
grok plugin install anchorbrowser --trust
```

Or straight from this repository:

```bash
grok plugin install anchorbrowser/anchor-mcp-plugin#grok --trust
```

Either server can be turned off in `/mcps` without disabling the plugin.

## Site actions

Verified deterministic actions for one site live at `https://api.anchorbrowser.io/v1/mcp/actions/<domain>`. The domain is part of the URL, so add them per site rather than through this plugin:

```bash
grok mcp add --transport http anchor-amazon https://api.anchorbrowser.io/v1/mcp/actions/amazon.com
```

## Network and credentials

Both servers are HTTPS endpoints on `api.anchorbrowser.io`. Authentication is OAuth sign-in with your Anchor account, handled by Grok on first connection; the plugin reads no environment variables or local files. Browser sessions run in ephemeral VMs in Anchor's cloud and are destroyed when they end.

Docs: https://docs.anchorbrowser.io/advanced/mcp
