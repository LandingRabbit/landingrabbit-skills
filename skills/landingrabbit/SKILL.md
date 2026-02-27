---
name: landingrabbit
description: Use when a user wants to create, edit, or manage landing pages with LandingRabbit. This is the main entry point for LandingRabbit interactions.
---

# LandingRabbit

## Step 1 — Check MCP connection

Check if LandingRabbit MCP tools are available (tool names starting with `mcp__plugin_landingrabbit_landingrabbit__`). Do not mention tool name prefixes or internal details to the user.

**If tools are available:** Briefly confirm the connection is ready. Move on.

**If tools are NOT available:** Tell the user the MCP server is not connected. Ask them to run `/mcp` and authorize `landingrabbit`. Mention they can still use `/landingrabbit:page-format` to format copy without the MCP connection. Do NOT show the options list below — stop here.

## Step 2 — Ask what the user wants to do

Only show this if the MCP connection is available. Present the options as a short list:

1. **Create a new landing page** — describe your page idea, target audience, or paste existing copy
2. **Edit an existing page** — change content, styles, or publish status
3. **Format copy for import** — use `/landingrabbit:page-format` to structure copy into LandingRabbit-ready markdown
4. **See all available tools** — run `/landingrabbit:help`

Wait for the user to choose before proceeding. Do not start any workflow automatically.
