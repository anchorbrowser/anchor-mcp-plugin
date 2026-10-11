# Anchor Actions

Hosted MCP server at `https://api.anchorbrowser.io/v1/mcp/actions/{domain}`. Sign in with your Anchor account on first use.

Every active action in Anchor's index for one site becomes a typed tool with the action's own parameter schema, for example `amazon-search-products`. Each run is deterministic code in an Anchor cloud browser with no LLM steps, so results are repeatable and cheap.

The domain is part of the URL, so this plugin holds one site per install. Cursor asks for `SITE_DOMAIN` at install; Claude Code asks when the plugin is enabled. Use a bare domain such as `amazon.com`, with no scheme or path.

Actions that need a signed-in account say so and take a `sessionId`. Create that session with an identity on the `anchor` plugin and pass its id.

To work with several sites at once, add each as its own MCP server with a name that carries the site, such as `anchor-amazon` and `anchor-linkedin`, each pointing at its own `/v1/mcp/actions/<domain>` URL. They share one sign-in, and tool names are prefixed with the site.

Data: tool calls go only to `api.anchorbrowser.io`.

Docs: https://docs.anchorbrowser.io/advanced/mcp#anchor-actions
