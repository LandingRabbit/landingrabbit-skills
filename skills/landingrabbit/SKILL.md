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

1. **Create a new page** — describe your page idea, share notes or a meeting transcript, or paste existing copy
2. **Edit an existing page** — change content, images, icons, styles, templates, custom section layouts, SEO metadata, tags, categories, collections, publish status, or recreate a section from a reference design
3. **Review your site content** — export all pages to a CSV file, or send a meeting transcript to find topics your pages do not answer
4. **Format copy for import** — use `/landingrabbit:page-format` to structure copy into LandingRabbit-ready markdown
5. **See all available tools** — run `/landingrabbit:help`

Wait for the user to choose before proceeding. Do not start any workflow automatically.
