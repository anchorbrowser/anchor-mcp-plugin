# Anchor

Hosted MCP server at `https://api.anchorbrowser.io/v1/mcp`. Sign in with your Anchor account on first use; there is no API key to paste and nothing to install. Every tool runs in Anchor's cloud, so nothing executes on your machine.

Start here if you want an agent to get work done on the web:

- Web tasks: `perform_web_task` runs a natural-language task in an isolated cloud browser; `get_web_task_status` polls the result.
- Site actions: `search_action_index`, `get_action_index`, `execute_action_index` find and run verified deterministic actions for known sites.
- Saved automations: `list_tasks`, `get_task`, `run_task`, `get_execution`.
- Managed logins: `create_identity`, `create_reauth_link`, `reauthenticate_identity`, `get_identity`, plus the `*_dynamic_auth` tools for step-by-step sign-in. Anchor handles MFA and keeps credentials in its vault; no tool returns them.
- Browser sessions: `create_session`, `get_session`, `end_session`, with residential proxies, stealth, and captcha solving.
- Docs and the rest of the API: `search_docs`, `read_doc`, `list_endpoints`, `get_endpoint`, `call_endpoint_read`, `call_endpoint_write`.

This server does not drive a browser step by step. For that, add the `anchor-browser` plugin, or connect a CDP client to the `cdp_url` returned by `create_session`.

Data: tool calls go only to `api.anchorbrowser.io`. Browser sessions run in ephemeral VMs that are destroyed when the session ends.

Docs: https://docs.anchorbrowser.io/advanced/mcp
