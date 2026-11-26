# Anchor Browser for Antigravity

One plugin, three hosted MCP servers. Sign in with your Anchor account on first use; there is no API key to paste and nothing runs on your machine.

| Server | URL | What it does |
| --- | --- | --- |
| `anchor` | `https://api.anchorbrowser.io/v1/mcp` | Web tasks, verified site actions for any site in the action index, saved automations, managed logins with MFA, browser sessions with proxies and captcha solving, and docs. |
| `anchor-browser` | `https://api.anchorbrowser.io/v1/mcp/browser` | Step-by-step control of a live Anchor browser: `anchor_navigate`, `anchor_snapshot`, `anchor_click`, `anchor_type`, screenshots, network and console logs, and Playwright code generation. |
| `anchor-actions` | `https://api.anchorbrowser.io/v1/mcp/actions` | The action index as its own server: `find_actions` lists verified deterministic actions for a site or a goal, and `run_action` runs one in an Anchor cloud browser. |

Start with `anchor` for anything that should just get done; use `anchor-browser` when the agent needs to drive the page itself, and `anchor-actions` when the run should be repeatable without an AI step.

## Install

```bash
agy plugin install https://github.com/anchorbrowser/anchor-mcp-plugin/tree/main/antigravity
```

Install this folder, not the repository root: the root also holds the Claude Code and Cursor plugins, and Antigravity would import each of those as a separate plugin.

Then run `/plugin` in the CLI, expand **anchorbrowser** under Installed, and choose **Sign in** for each server. In the Antigravity App, use **Customizations > Installed**.

The tools an agent uses most (`perform_web_task`, `create_session`, the action index tools, `find_actions`, `run_action`, and the core `anchor_*` browser tools) are loaded up front, so the agent calls them directly. The rest load on demand.

## Site actions

The `anchor-actions` server finds and runs verified actions for any site with `find_actions` and `run_action`, so there is nothing to set up per site. The `anchor` server reaches the same index with `search_action_index` and `execute_action_index`.

To expose one site's actions as their own typed tools instead, add that site as an MCP server:

```bash
agy mcp add anchor-amazon https://api.anchorbrowser.io/v1/mcp/actions/amazon.com
```

## Network and credentials

All three servers are HTTPS endpoints on `api.anchorbrowser.io`. Authentication is OAuth sign-in with your Anchor account; the plugin reads no environment variables or local files. Browser sessions run in ephemeral VMs in Anchor's cloud and are destroyed when they end.

Docs: https://docs.anchorbrowser.io/advanced/mcp
