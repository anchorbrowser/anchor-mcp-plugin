# Anchor Browser for Antigravity

One plugin, two hosted MCP servers. Sign in with your Anchor account on first use; there is no API key to paste and nothing runs on your machine.

| Server | URL | What it does |
| --- | --- | --- |
| `anchor` | `https://api.anchorbrowser.io/v1/mcp` | Web tasks, verified site actions for any site in the action index, saved automations, managed logins with MFA, browser sessions with proxies and captcha solving, and docs. |
| `anchor-browser` | `https://api.anchorbrowser.io/v1/mcp/browser` | Step-by-step control of a live Anchor browser: `anchor_navigate`, `anchor_snapshot`, `anchor_click`, `anchor_type`, screenshots, network and console logs, and Playwright code generation. |

Start with `anchor` for anything that should just get done; use `anchor-browser` when the agent needs to drive the page itself.

## Install

```bash
git clone https://github.com/anchorbrowser/anchor-mcp-plugin
agy plugin install ./anchor-mcp-plugin/antigravity
```

Install the `antigravity` folder, not the repository root: the root also holds the Claude Code and Cursor plugins, and Antigravity would import each of those as a separate plugin.

Then run `/plugin` in the CLI, expand **anchorbrowser** under Installed, and choose **Sign in** for each server. In the Antigravity App, use **Customizations > Installed**.

The tools an agent uses most (`perform_web_task`, `create_session`, the action index tools, and the core `anchor_*` browser tools) are loaded up front, so the agent calls them directly. The rest load on demand.

## Site actions

The `anchor` server already finds and runs verified actions for any site with `search_action_index` and `execute_action_index`, so there is nothing to set up per site.

To expose one site's actions as their own typed tools instead, add that site as an MCP server:

```bash
agy mcp add anchor-amazon https://api.anchorbrowser.io/v1/mcp/actions/amazon.com
```

## Network and credentials

Both servers are HTTPS endpoints on `api.anchorbrowser.io`. Authentication is OAuth sign-in with your Anchor account; the plugin reads no environment variables or local files. Browser sessions run in ephemeral VMs in Anchor's cloud and are destroyed when they end.

Docs: https://docs.anchorbrowser.io/advanced/mcp
