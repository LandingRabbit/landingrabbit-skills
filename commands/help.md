---
name: help
description: List all LandingRabbit skills and MCP tools with connection status
---

# LandingRabbit Help

## Step 1 — Check MCP connection

Check if LandingRabbit MCP tools are available (tool names starting with `mcp__plugin_landingrabbit_landingrabbit__`). Do not mention tool name prefixes or internal details to the user.

**If tools are available:** Tell the user the MCP server is connected and ready.

**If tools are NOT available:** Tell the user the MCP server is not connected. Ask them to run `/mcp` and authorize `landingrabbit`.

## Step 2 — Show tables

Output the skills table exactly as shown below:

```
┌────────────────────────────────┬────────────────────────────────────────────┐
│ Command                        │ Description                                │
├────────────────────────────────┼────────────────────────────────────────────┤
│ /landingrabbit:landingrabbit   │ Get started — create, edit, manage pages   │
│ /landingrabbit:page-format     │ Format copy into LandingRabbit-ready md    │
│ /landingrabbit:help            │ This reference screen                      │
└────────────────────────────────┴────────────────────────────────────────────┘
```

If MCP tools are available, also output this table:

```
┌────────────────────────────────┬────────────────────────────────────────────┐
│ Tool                           │ Description                                │
├────────────────────────────────┼────────────────────────────────────────────┤
│ create_landing_page            │ Create a full page in one call             │
│ plan_your_landing_page         │ Determine best page type                   │
│ create_detailed_plan           │ Build value proposition plan               │
│ generate_landing_page          │ Generate final page and get URL            │
│ create_page_from_content       │ Convert existing copy to a page            │
│ migrate_blog_content           │ Import blog posts into LandingRabbit       │
│ replace_links                  │ Bulk replace URLs across pages             │
│ list_workspace_pages           │ List all pages with status                 │
│ edit_page_content              │ Edit sections and page content             │
│ edit_page_styles               │ Edit visual styles and layouts             │
│ set_page_publish_state         │ Publish or unpublish a page                │
│ orchestrator_chat              │ Natural language page editing              │
└────────────────────────────────┴────────────────────────────────────────────┘
```

If MCP tools are NOT available, show instead:

```
MCP Tools — not connected. Run /mcp and authorize landingrabbit.
```

Output the tables verbatim inside fenced code blocks. Do not reformat, reorder, or regenerate them.
