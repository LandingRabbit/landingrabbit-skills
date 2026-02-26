# LandingRabbit Skills

AI skills for formatting landing page copy into [LandingRabbit](https://landingrabbit.com)-ready markdown.

## What's included

| Component | Description |
|---|---|
| `landingrabbit-page-format` (skill) | Converts landing page copy into structured markdown that LandingRabbit can parse and render. |
| LandingRabbit MCP server | Connects to the LandingRabbit API via OAuth so Claude can manage pages, sites, and content directly. |

### Supported section types

| Section | Use for |
|---|---|
| `hero` | Opening value proposition and primary CTA |
| `trustedBy` | Social proof logos and credibility |
| `steps` | Process flows, pain points, checklists, metrics |
| `collection` | Feature/benefit/service blocks with repeatable items |
| `testimonials` | Customer proof quotes |
| `pricing` | Plan comparison tables |
| `comparison` | Before/after or contrasting list groups |
| `faq` | Question-and-answer pairs |
| `cta` | Focused conversion sections |
| `custom` | Free-form mixed content (about us, narratives, embeds) |

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

### Claude Code

Install through Claude Code marketplaces:

```text
/plugin marketplace add LandingRabbit/landingrabbit-skills
/plugin install landingrabbit-skills@landingrabbit
```

If you already have this repository locally, you can add it from a local path instead:

```text
/plugin marketplace add /path/to/landingrabbit-skills
/plugin install landingrabbit-skills@landingrabbit
```

Marketplace updates for third-party sources are manual by default. To pull the latest version:

```text
/plugin marketplace update landingrabbit
```

If needed, update the installed plugin after updating the marketplace:

```text
/plugin update landingrabbit-skills@landingrabbit
```

### Codex

```bash
git clone https://github.com/LandingRabbit/landingrabbit-skills.git ~/.codex/landingrabbit-skills
mkdir -p ~/.agents/skills
ln -s ~/.codex/landingrabbit-skills/skills ~/.agents/skills/landingrabbit-skills
```

See [.codex/INSTALL.md](.codex/INSTALL.md) for Windows instructions and details.

## MCP server

This plugin bundles an MCP (Model Context Protocol) connection to the LandingRabbit API. On first use, Claude Code will open an OAuth flow in your browser so you can authorize access to your LandingRabbit account. After that, Claude can interact with LandingRabbit on your behalf.

Run `/mcp` inside Claude Code to verify the `landingrabbit` server appears and is connected.

## Usage

Give the skill your landing page copy — headlines, descriptions, CTAs, testimonials, pricing, FAQ, etc. — and it returns a single markdown document formatted for LandingRabbit import.

The skill preserves your content and tone. It only restructures the copy into LandingRabbit-compatible sections with suggested layouts.

## License

[MIT](LICENSE)
