# LandingRabbit Skills

AI skills for formatting landing page copy into [LandingRabbit](https://landingrabbit.com)-ready markdown.

## What's included

| Component                | Description                                                                          |
| ------------------------ | ------------------------------------------------------------------------------------ |
| `landingrabbit` (skill)  | Main entry point — guides you through creating, editing, or managing pages           |
| `page-format` (skill)    | Converts landing page copy into structured markdown that LandingRabbit can parse     |
| `help` (command)         | Lists all available skills and MCP tools with connection status                      |
| LandingRabbit MCP server | Connects to the LandingRabbit API via OAuth so Claude can manage pages, templates, styles, custom layouts, tags, and categories directly |

### Supported section types

| Section        | Use for                                                |
| -------------- | ------------------------------------------------------ |
| `hero`         | Opening value proposition and primary CTA              |
| `trustedBy`    | Social proof logos and credibility                     |
| `steps`        | Process flows, pain points, checklists, metrics        |
| `collection`   | Feature/benefit/service blocks with repeatable items   |
| `testimonials` | Customer proof quotes                                  |
| `pricing`      | Plan comparison tables                                 |
| `comparison`   | Before/after or contrasting list groups                |
| `faq`          | Question-and-answer pairs                              |
| `cta`          | Focused conversion sections                            |
| `custom`       | Free-form mixed content (about us, narratives, embeds) |
| `feed`         | Dynamic post lists from a workspace collection          |

### Content fields

Sections use markdown-native structure:

- Eyebrow: `[eyebrow]: ...`
- Icon (collection `boxes-icons`): `[icon]: ...`
- Smallprint: `[smallprint]: ...`
- Titles: `#`, `##`, `###`
- Body: plain markdown paragraphs
- CTAs: `[Label](url)` — one per line
- Images: `![Alt](url)`
- Embeds: fenced `html` blocks
- Styled bullets: `✅`, `✓`, `☑`, `❌`, `✗`, `⭐`, `→`, `➡️`, `-`, `*`, `•`, or `:icon:` prefixes
- Nested boxes/testimonials: `[boxes]` and `[testimonial]` where supported
- Bottom CTAs: `[bottomCtas]` or `[bottomCta]` for feed

### Layout options

Most sections support a `suggestedLayout` directive:

```
hero          → horizontal, horizontal-reversed, vertical; mediaVisibility; imageFit; style
steps         → stepDecoration; mediaVisibility; mediaPosition; imageFit; stepIcon; style
collection    → alternate, boxes, boxes-text, boxes-icons; sectionHeaderPosition; dividers; imageFit; style
testimonials  → carousel, grid; carouselAutoplay; sectionHeaderPosition; imageFit; style
comparison    → boxes-text, boxes, boxes-icons; imageFit
cta           → default, embed; mediaVisibility; imageFit; style
custom        → left, middle; style
pricing       → pricingSwitch; style
faq           → sectionHeaderPosition; style
trustedBy     → logosScroll; logosScrollSpeed; style
feed          → boxes, boxes-text, alternate; collection; itemCount; showDescription; showTimestamp; readMoreText
```

## Install

### Claude Code (CLI)

Run these in your terminal:

```bash
claude plugin marketplace add LandingRabbit/landingrabbit-skills
```

```bash
claude plugin install landingrabbit@landingrabbit
```

To update, pull the latest marketplace version first:

```bash
claude plugin marketplace update landingrabbit
```

If the marketplace update pulled a newer version, update the installed plugin too:

```bash
claude plugin update landingrabbit@landingrabbit
```

**Tip:** To enable auto-updates, open `/plugin` inside a Claude session, go to **Marketplaces**, select **landingrabbit**, and choose **Enable auto-update**.

### Claude for Desktop

Run these inside a Claude session:

```text
/plugin marketplace add LandingRabbit/landingrabbit-skills
```

```text
/plugin install landingrabbit@landingrabbit
```

### Local path

If you already have this repository locally, you can add it from a local path instead of the GitHub source.

**CLI:**

```bash
claude plugin marketplace add /path/to/landingrabbit-skills
```

```bash
claude plugin install landingrabbit@landingrabbit
```

**Desktop:**

```text
/plugin marketplace add /path/to/landingrabbit-skills
```

```text
/plugin install landingrabbit@landingrabbit
```

### Connect the MCP server

The plugin includes an MCP server that connects to the LandingRabbit API. On first use, Claude will open an OAuth flow in your browser so you can authorize access to your LandingRabbit account.

To verify the connection, run `/mcp` inside Claude and check that the `landingrabbit` server appears.

### Get started

Run `/landingrabbit` inside Claude to get started.

## Uninstall

### Claude Code (CLI)

```bash
claude plugin uninstall landingrabbit@landingrabbit
```

```bash
claude plugin marketplace remove landingrabbit
```

### Claude for Desktop

```text
/plugin uninstall
```

Select `landingrabbit` from the list, then remove the marketplace source:

```text
/plugin marketplace remove landingrabbit
```

## Usage

Run `/landingrabbit:landingrabbit` to get started. It checks your MCP connection and walks you through what you can do.

With the MCP server connected, Claude can inspect workspace pages, look up a specific page by slug, update SEO metadata, edit existing page content, manage tags and categories, and manage page images (upload, search, and place) directly from chat.

Claude can also manage section style templates through MCP: inspect the active template/brand/base layers for a layout, create or update section templates, mark a template as the default for its layout, delete a template on explicit request, and update brand styles for an entire section group.

When a section needs a layout that isn't available out of the box, Claude can build a fully custom section design through MCP: start from a placeholder-based starter layout, save or update the custom layout for a section, and revert back to standard rendering — all while keeping chosen parts of the section editable in the editor.

In some multi-locale workspaces, Claude may ask you to detach inherited styles before applying locale-specific brand style changes.

To format existing copy into LandingRabbit-ready markdown, use `/landingrabbit:page-format`. Give it your landing page copy — headlines, descriptions, CTAs, testimonials, pricing, FAQ, feed sections, article content, etc. — and it returns a single markdown document ready to import. The skill preserves your content and tone.

Run `/landingrabbit:help` to see all available skills and MCP tools.

## License

[MIT](LICENSE)
