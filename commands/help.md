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
│ create_page                    │ Create a new page from ideas or materials  │
│ create_page_from_content       │ Convert existing copy to a page            │
│ get_page_format_guide          │ Read the markdown format for page imports  │
│ migrate_blog_content           │ Import blog posts into LandingRabbit       │
│ replace_links                  │ Bulk replace URLs across pages             │
│ list_workspace_pages           │ List all published and drafts              │
│ export_pages_csv               │ Export all pages to a CSV file             │
│ send_meeting_transcripts       │ Find content gaps from meeting transcripts │
│ update_page_metadata           │ Batch update page SEO metadata             │
│ manage_tags                    │ List, create, or delete workspace tags     │
│ manage_categories              │ List, create, or delete categories         │
│ edit_page_content              │ Edit sections and page content             │
│ edit_page_styles               │ Edit visual styles and layouts             │
│ manage_templates               │ Plan designs, manage templates and styles  │
│ custom_design                  │ Design a custom section layout             │
│ set_page_publish_state         │ Publish or unpublish a page                │
│ edit_page_images               │ Upload, search, and place images           │
│ search_icons                   │ Find icons for section content             │
│ orchestrator_chat              │ Choose the right tool for page edits       │
└────────────────────────────────┴────────────────────────────────────────────┘
```

If MCP tools are NOT available, show instead:

```
MCP Tools — not connected. Run /mcp and authorize landingrabbit.
```

Output the tables verbatim inside fenced code blocks. Do not reformat, reorder, or regenerate them.
