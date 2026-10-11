# Anchor Browser

Hosted MCP server at `https://api.anchorbrowser.io/v1/mcp/browser`. Sign in with your Anchor account on first use. The browser runs in Anchor's cloud, so there is no browser driver to install locally.

Step-by-step control of a live browser through `anchor_*` tools: `anchor_navigate`, `anchor_snapshot`, `anchor_click`, `anchor_type`, `anchor_select_option`, `anchor_press_key`, `anchor_take_screenshot`, `anchor_network_requests`, `anchor_console_messages`, tab management, and `anchor_generate_playwright_code`. Element references come from accessibility snapshots, so no vision model is needed.

The first tool call opens a new session. To attach to a session you created with the `anchor` plugin, for example one signed in with an identity, send its id in an `anchor-session-id` header. Every result echoes the session id so `perform_web_task` and site actions can continue in the same browser.

Use it to explore a site, debug a flow, or record steps into Playwright code. For one-shot tasks and authenticated work, use the `anchor` plugin.

Data: tool calls go only to `api.anchorbrowser.io`; the cloud browser loads whatever pages you navigate to.

Docs: https://docs.anchorbrowser.io/advanced/mcp#anchor-browser
