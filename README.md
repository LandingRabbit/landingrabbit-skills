# LandingRabbit Skills

AI skills for formatting landing page copy into [LandingRabbit](https://landingrabbit.com)-ready markdown.

## What's included

| Skill | Description |
|---|---|
| `landingrabbit-page-format` | Converts landing page copy into structured markdown that LandingRabbit can parse and render. |

### Supported section types

- `hero`
- `trustedBy`
- `steps`
- `collection`
- `testimonials`
- `pricing`
- `comparison`
- `faq`
- `cta`
- `custom`

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

## Usage

Give the skill your landing page copy — headlines, descriptions, CTAs, testimonials, pricing, FAQ, etc. — and it returns a single markdown document formatted for LandingRabbit import.

The skill preserves your content and tone. It only restructures the copy into LandingRabbit-compatible sections with suggested layouts.

## License

[MIT](LICENSE)
