# Zarla — build, edit and publish websites from Gemini CLI

Zarla is connected as an MCP server (endpoint: https://www.zarla.com/api/mcp). Use its tools to create, edit and publish the user's websites at https://www.zarla.com. The user signs in with their Zarla account when the connection is first used (OAuth — there are no API keys to configure).

## How to work with it

- Start with `list_sites` to see the user's websites. An account with no sites returns an empty list and names `create_site` as the next step — offer to build one from a one-sentence description of the business.
- Every edit tool (`update_block`, `update_design`, `set_logo`, `add_page`, …) changes the user's **private draft**. Nothing reaches the live site until `publish_site`. Say so when you report an edit, and offer `show_site_preview` (a preview link) so the user can look before publishing.
- `publish_site` replaces what is currently live. Confirm with the user before calling it. On the Free plan the tool returns a link to the plans page instead of publishing — relay the link; publishing resumes automatically after the upgrade.
- For photos and logos the user shares, use `request_image_upload` → PUT the bytes → `finalize_image_upload`, then `set_logo` or `update_block`.
- Read the tool descriptions — they state exactly what each tool does (and, where it matters, what it costs). `create_site` builds the home page; add further pages with `add_page`.

## Example requests

- "Build a website for my mobile dog-grooming business in Denver."
- "Rewrite my homepage headline to sound more premium, and add a testimonials section."
- "Add a page for our spring gutter-cleaning special and publish my site."
- "What websites do I have on Zarla?"
- "Show me my website."
- "Give my site a warmer, more welcoming look."

Setup guide for every client: https://www.zarla.com/help/connect-claude-and-ai-agents
