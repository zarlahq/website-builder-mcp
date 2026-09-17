# Installing the Zarla MCP server (for AI agents such as Cline)

Zarla is a **remote** MCP server. There is nothing to download, build or run locally. The normal path is a browser sign-in with the user's Zarla account; an API token exists only as a fallback for clients that cannot complete that sign-in.

- Endpoint: `https://www.zarla.com/api/mcp`
- Transport: Streamable HTTP
- Authentication: OAuth 2.1 — the user signs in to their Zarla account in the browser the first time the connection is used. Clients that cannot complete an OAuth sign-in can use a personal API token from https://www.zarla.com/connect as an `Authorization: Bearer <token>` header instead.

## Cline

1. Open **MCP Servers → Remote Servers** in Cline.
2. Server name: `zarla`. Server URL: `https://www.zarla.com/api/mcp`. Transport: **Streamable HTTP**. Click **Add Server**.
3. If Cline cannot open the sign-in, create an API token on https://www.zarla.com/connect and add it as a header:

```json
{
  "mcpServers": {
    "zarla": {
      "type": "streamableHttp",
      "url": "https://www.zarla.com/api/mcp",
      "headers": { "Authorization": "Bearer <your Zarla API token>" }
    }
  }
}
```

Treat the token like a password; it can be revoked from the same page.

## Any other MCP client

Add a remote server with the URL `https://www.zarla.com/api/mcp` and sign in when prompted. Per-client walkthroughs (Claude, Claude Code, ChatGPT, Cursor, Gemini CLI): https://www.zarla.com/help/connect-claude-and-ai-agents

## First things to try

- `list_sites` — the user's websites (empty list → offer `create_site`).
- "Build a website for my mobile dog-grooming business in Denver."
- "Show me my website." → `show_site_preview` returns a preview link.
- "Publish my site." → `publish_site` (replaces the live site; confirm first).
