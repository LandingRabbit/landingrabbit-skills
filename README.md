# LandingRabbit Skills

AI skills for formatting landing page copy into [LandingRabbit](https://landingrabbit.com)-ready markdown.

## What's included

| Component                | Description                                                                          |
| ------------------------ | ------------------------------------------------------------------------------------ |
| `landingrabbit` (skill)  | Main entry point — guides you through creating, editing, or managing pages           |
| `page-format` (skill)    | Converts landing page copy into structured markdown that LandingRabbit can parse     |
| `help` (command)         | Lists all available skills and MCP tools with connection status                      |
| LandingRabbit MCP server | Connects to the LandingRabbit API via OAuth so Claude can manage pages and content directly |

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
- Styled bullets: `✅`, `❌`, or `-` prefixes

### Layout options

Most sections support a `suggestedLayout` directive:

```
hero          → horizontal, horizontal-reversed, vertical
steps         → stepDecoration: number, none, check, star, arrow, success, destructive
collection    → alternate, boxes, boxes-text, boxes-icons
testimonials  → carousel, grid
comparison    → boxes-text
cta           → default, embed
custom        → left, middle
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

To format existing copy into LandingRabbit-ready markdown, use `/landingrabbit:page-format`. Give it your landing page copy — headlines, descriptions, CTAs, testimonials, pricing, FAQ, etc. — and it returns a single markdown document ready to import. The skill preserves your content and tone.

Run `/landingrabbit:help` to see all available skills and MCP tools.

## License

[MIT](LICENSE)
