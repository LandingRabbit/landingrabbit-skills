---
name: page-format
description: Use this skill when a marketer is drafting page copy and wants page structure and copy that map cleanly to LandingRabbit-supported sections and content items.
---

# LandingRabbit Page Format Skill

## Purpose

Use this skill when a user is writing landing page copy and wants:

- Use the LLM service of their choice for content brainstorming and content creation.
- Get the copy in a markdown format that LandingRabbit can parse reliably and turn into a page.
- Use only supported LandingRabbit section types and content fields so that users can easily import their ready page structure and copy

## Step-by-step task

Your task is to read user's ready landing page copy and format it into the LandingRabbit-Ready Markdown.

1. Check if LandingRabbit MCP tools are available (tool names starting with `mcp__plugin_landingrabbit_landingrabbit__`). Do not mention tool name prefixes or internal details to the user. If they are not available, briefly let the user know and suggest running `/mcp` to check the connection. Keep this to one sentence — do not block the formatting task.
2. Review the planned copy text and page structure
3. Match the copy with the available sections and content items
4. Provide your answer in LandingRabbit-ready markdown following the example answers

## Important instructions

- Provide your answer as a single document that is easy to copy and paste to LandingRabbit
- Avoid making changes to user's text and section order
- Only share the LandingRabbit-ready markdown with section types and suggested layouts. Don't add any additional comments or explanations in your answer
- Examples in this skill are only to show the supported structure. Preserve user's content and tone of voice
- You don't need to use all available sections and content items. Respect the user's ready content
- Use `---` only between sections in the final answer, never inside section content blocks
- Do not output URL-only lines (e.g. `/schedule-a-call`, `https://...`) as normal copy text; keep URLs only inside markdown links `[text](url)`

## Available sections

- `hero`: Opening value proposition and primary conversion action.
- `trustedBy`: Social proof section for logos and credibility content.
- `steps`: Process, checklist, or sequence of actions/outcomes, or problems customers face.
- `collection`: Structured service/feature/benefit blocks with repeatable items.
- `testimonials`: Customer proof quotes
- `pricing`: Plan comparison table
- `comparison`: Before/after or current/future contrast.
- `faq`: Question-and-answer section to handle objections.
- `cta`: Focused conversion section, often near the end.
- `custom`: Free-form mixed content (headings, text blocks, image, embed, CTA).

## Response format for sections

Provide the section type in your answer (e.g., Section type: `hero`)

For each section, use markdown-native structure like this:

- Eyebrow: `[eyebrow]: ...`
- Icon (for `collection` + `boxes-icons` items): `[icon]: ...` (leave empty when user should pick icons in UI)
- Smallprint: `[smallprint]: ...`
- Section or item title: `#`, `##`, `###`
- Description/body: plain markdown paragraphs
- CTA links: one per line (each on its own line), e.g.:
  `[Primary CTA](url)`
  `[Secondary CTA](url)`
- Images: `![Alt](url)`
- Embeds/forms/widgets: fenced `html` blocks

Use `---` between sections.

## Bullet Lists in Descriptions

In any description or subtitle field, use these prefixes to add styled bullet lists:

- `✅ Text` - success (green checkmark); use for benefits, features, positive outcomes
- `❌ Text` - destructive (red X); use for problems, pain points, negative items
- `- Text` - standard bullet (dot); use for neutral lists

Mix bullet types and regular paragraphs in the same field. Consecutive lines with the same icon become one list.

**Example - hero description with success bullets:**

```markdown
# Your page headline

✅ Pages live in 5 mins
✅ Loved by 200+ teams
✅ GDPR-friendly

[Get started](/signup)
```

## Suggested Layout

For sections that support multiple layouts, add `suggestedLayout:` on its own line before the section content.

---

### Hero

- `horizontal` _(default)_ - text left, media right
- `horizontal-reversed` - media left, text right
- `vertical` - centered text, no media or media below

---

### Steps

`stepDecoration` controls the icon shown beside each item. Add it before the section content.

- `number` _(default)_ - numbered; use for sequential process steps
- `none` - no icon; use for plain content lists
- `check` - checkmark; use for feature checklists and "what's included" lists
- `star` - star; use for highlights and notable achievements
- `arrow` - arrow; use for directional flows and "next step" sequences
- `success` - filled circle check; use for benefits and positive outcomes
- `destructive` - filled circle X; use for problems and pain points

If steps item lines already start with emoji markers (for example `😩`, `✅`, `🚀`), set `stepDecoration: none`.
If `stepDecoration` is not `none`, remove leading emoji/icon markers from step lines.

---

### Collection

- `alternate` - narrative benefit blocks (each item: title + paragraph, alternating sides)
  → Benefits, Value propositions, Solutions, "Why choose us"
- `boxes` - feature grid with per-item images
  → Features, Integrations, Technical capabilities
- `boxes-text` - text-only feature grid, no images
  → Use cases, Capability lists, Short feature summaries
- `boxes-icons` - icon grid (icon handled separately from text content)
  → Quick-scan feature highlights

Use 'alternate' when items are narrative and outcome-focused.
Use 'boxes' or 'boxes-text' when items are factual and scannable.
Use 'boxes-icons' only when each item is title + description and icon is provided via `[icon]: ...`.
When using `boxes-icons`, do NOT add item `[eyebrow]: ...` lines.
For `boxes-icons`, leave icon value empty by default (`[icon]:`) so user can choose icons in UI.

---

### Testimonials

- `carousel` _(default)_ - horizontal scroll, best for 3+ testimonials
- `grid` - all testimonials visible at once, best for 2-4

---

### Comparison

- `boxes-text` _(default)_ - side-by-side text-only comparison

Do not include leading `✅`/`❌`/emoji icons in comparison bullet lines.
Use plain text bullet lines; LandingRabbit renders comparison icons automatically.

---

### CTA

- `default` _(default)_ - centered title, description, and buttons
- `embed` - title and buttons with image or embed alongside

---

### Custom

- `left` _(default)_ - left-aligned, article or blog style
- `middle` - centered, landing page style

## Section Guide

### 1) Hero (`type: 'hero'`)

#### Purpose

Open with the primary promise, context, and next action.

#### Section fields

- `eyebrow`
- `title`
- `description`
- `ctas`
- `smallprint`
- Image: `![Alt text](url)` - renders in the image slot
- Embed: fenced `html` block with `<iframe>` - renders in the embed slot

#### Hero example with a video

```markdown
[eyebrow]: B2B Website Builder

# Turn your ideas into marketing pages in 10 minutes

You know your customers and what they need. LandingRabbit turns that knowledge into landing pages, blog posts, and full websites.

[Video: Product walkthrough](https://example.com/product-demo.mp4)

[Start your free trial](https://example.com/signup)
[Book demo](https://example.com/demo)

[smallprint]: No credit card needed. Join 200+ teams creating pages.
```

#### Hero example with an image

```markdown
[eyebrow]: B2B Website Builder

# Build campaign pages your team can launch this week

Create landing pages from ideas, sales materials, and product docs without starting from a blank page.

![LandingRabbit editor preview](https://example.com/hero-image.webp)

[Start your free trial](https://example.com/signup)
[See examples](https://example.com/examples)

[smallprint]: No credit card needed. Publish your first page in minutes.
```

#### Hero example with an embed

````markdown
[eyebrow]: B2B Website Builder

# See how teams publish pages faster with LandingRabbit

Watch a quick walkthrough to understand how drafting, editing, and publishing work in one flow.

```html
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/abc123"
  title="LandingRabbit walkthrough"
  frameborder="0"
  allowfullscreen
></iframe>
```

[Start your free trial](https://example.com/signup)
[Book demo](https://example.com/demo)

[smallprint]: Join 200+ teams building and publishing campaign pages.
````

### 2) Steps (`type: 'steps'`)

#### Purpose

- Use for: Lists and steps ("How it works", "Pain points", "Benefits at a glance")
- Can be sequential (process steps) OR parallel (metrics, achievements, features list)
- Do NOT use `steps` for two opposing list groups such as:
  - "Say goodbye to ... / And hello to ..."
  - "Before ... / After ..."
  - "Without ... / With ..."
    Use `comparison` for those.
- Examples:
  - Sequential: "How it works", Process steps, Timeline, Methodology
  - Parallel: Metrics/results, Statistics, Achievement highlights, Quick facts, Case study results

#### Section header fields

- `eyebrow`
- `title`
- `subtitle`
- `ctas`
- `stepDecoration` (see Suggested Layout guide)
- Image: `![Alt text](url)` - renders beside the steps list
- Embed: fenced `html` block with `<iframe>` - renders beside the steps list

#### Item fields (structured)

- `eyebrow`
- `title`
- `description`
- `ctas`

#### Problem section pain points (without item descriptions) example

```markdown
[eyebrow]: Problem

## You know you need new pages, but content creation keeps falling behind

1. Creating new pages is a hassle and a time drain.
2. Other tasks always feel more urgent than website updates.
3. Every update risks inconsistency across channels.
```

#### Problem section pain points (with item descriptions) example

```markdown
[eyebrow]: Problem

## Why teams delay launching new pages

Launching new pages is incredibly hard.

[eyebrow]: Speed

### Slow page creation workflow

Teams jump between docs, design tools, and dev queues before anything goes live.

[eyebrow]: Priorities

### Competing priorities

Campaign pages get deprioritized because production is heavy and hard to repeat.

[eyebrow]: Messaging

### Inconsistent messaging

Updates across ads, pages, and sales assets drift when the process is fragmented.
```

#### Steps with check decoration example

- `stepDecoration`: `check`

```markdown
[eyebrow]: What's included

## Everything in one place

- Unlimited pages
- Custom domain publishing
- AI section generation
- Team collaboration
```

### 3) Collection (`type: 'collection'`)

#### Purpose

- Use for: Structured content with items that have both subtitle AND description
- Examples: Features, Benefits, Services, Integrations, Value propositions
- Can appear multiple times. Each distinct section becomes a separate collection

#### Section header fields

- `eyebrow`
- `title`
- `description`
- `ctas`

#### Item fields

- `eyebrow`
- `subtitle`
- `description`
- `ctas`
- Image: `![Alt text](url)` - supported for `alternate` and `boxes` layouts

#### Collection with features example

- `suggestedLayout`: `boxes`

```markdown
[eyebrow]: Features

## Build pages faster with fewer bottlenecks

Create pages that prospects love and search engines find.

[eyebrow]: AI Drafting

### Generate full page structures

Create complete first drafts from a short campaign brief.

[eyebrow]: Brand controls

### Keep messaging consistent

Apply your tone, value props, and key claims across sections.

[eyebrow]: Publishing

### Go live on your domain

Publish quickly and iterate without rebuilding from scratch.
```

#### Collection with benefits

- `suggestedLayout`: `alternate`

```markdown
[eyebrow]: Benefits

## Why teams switch to LandingRabbit

[Start your free trial](https://example.com/signup)

[eyebrow]: Speed to launch

### Ship campaign pages in hours

Move from idea to published page in one streamlined workflow.

[eyebrow]: Better conversion focus

### Keep every section outcome-oriented

Structure pages around pain points, proof, and clear CTA paths.

[eyebrow]: Team alignment

### Reduce handoff friction

Marketers and stakeholders work from one source of truth.
```

#### Collection with icons

- `suggestedLayout`: `boxes-icons`

```markdown
## Built for modern B2B campaign teams

[icon]:

### Launch fast

Create campaign-ready drafts in minutes.

[icon]:

### Match audience intent

Build pages tailored to keyword, industry, or use case.

[icon]:

### Stay on-brand

Maintain voice, positioning, and visual direction across pages.
```

#### Collection boxes with text only

- `suggestedLayout`: `boxes-text`

```markdown
[eyebrow]: Use cases

## Create pages from materials you already have

### Keywords

Turn SEO and ad keywords into dedicated pages

### Product docs

Convert specs into clear solution pages

### Sales notes

Create account-specific ABM pages from call insights
```

### 4) Testimonials (`type: 'testimonials'`)

#### Purpose

- Use for: Customer testimonials, quotes, case studies
- Can include multiple testimonials in one section
- Can appear multiple times if user has multiple testimonial sections

#### Section header fields

- `eyebrow`
- `title`

#### Item fields

- `quote`
- `name`
- `role`
- `company`

#### Example (all fields)

```markdown
## What our customers say

"We cut campaign page production from two weeks to one day.”
Maya Chen
Growth Lead
Northbeam AI

“Publishing became a same-day workflow for our team.”
Jonas Ranta
Demand Gen Manager
ScaleForge
```

### 5) Pricing (`type: 'pricing'`)

#### Purpose

- Use for: Pricing tables / plans
- Use pricing when the user clearly provides plan names + prices (and optionally feature bullets). Consider custom section in other cases
- In content, use `✅` for bullets

#### Section header fields

- `eyebrow`
- `title`
- `description`
- `ctas`

#### Item fields

- `eyebrow`
- `h3` (plan name)
- `price`
- `subtitle`
- `description`
- `cta`

#### Pricing section example

```markdown
[eyebrow]: Pricing

## Plans for every growth stage

Pick the plan that matches your campaign volume.

[Compare all plans](https://example.com/pricing)

[eyebrow]: For lean teams

### Starter

$49/month

Launch quickly

✅ 5 active pages
✅ AI section generation
✅ Custom domain publishing

[Start Starter](https://example.com/signup)

[eyebrow]: Most popular

### Growth

$149/month

Scale campaigns with collaboration

✅ 25 active pages
✅ Team collaboration
✅ Advanced exports

[Start Growth](https://example.com/signup)
```

### 6) Comparison (`type: 'comparison'`)

#### Purpose

- Show a clear before/after or current/future contrast.
- Use `❌` bullets for `Before` items.
- Use `✅` bullets for `After` items.
- Also use `comparison` when one section has two contrasting bullet groups (e.g. "say goodbye to" and "hello to").

#### Section header fields

- `eyebrow`
- `title`
- `subtitle`
- `ctas`

#### Item fields

- `eyebrow`
- `subtitle`
- `descriptions[]`
- `ctas`

#### Comparison section example

```markdown
[eyebrow]: Before vs after

## What changes with LandingRabbit

A side-by-side view of your workflow shift.

[See migration guide](https://example.com/migration)

### Legacy process

- ❌ Copy and design in separate tools
- ❌ Slow review loops
- ❌ Delayed launches

### LandingRabbit workflow

- ✅ One place for structure, copy, and publish
- ✅ Faster iteration cycles
- ✅ Better consistency across campaigns
```

### Comparison from "goodbye / hello" copy pattern

```markdown
[eyebrow]: Effortless efficiency

## If your team can use email and WhatsApp, they can use HotKup

### Say goodbye to

- Endless status meetings and chasing updates
- Duplicating work across tools
- Tasks falling through the cracks
- Hefty, modular price tags

### Hello to

- Everything in one place — no more "which WhatsApp group was that in?"
- Update once, everyone sees it — no more copying between sheets and apps
- Everyone knows what needs doing next — work actually gets done
- One price. Full functionality. Designed for SMMEs.
```

### 7) FAQ (`type: 'faq'`)

#### Purpose

- Use for: Question and answer pairs
- Only include if user explicitly provides Q&A content

#### Section fields

- `eyebrow`
- `title`
- `subtitle`
- `ctas`

#### Item fields

- `question`
- `answer`

#### Example

```markdown
[eyebrow]: FAQ

## Questions teams ask before switching

Short answers to common blockers.

### Can we publish on our own domain?

Yes. You can publish pages to your custom domain.

### Can we export content and designs?

Yes. Export to Webflow, Figma, JSON, Markdown, PDF, and PNG.

### Is this only for marketers?

No. Growth, product marketing, and content teams use it collaboratively.
```

### 8) CTA (`type: 'cta'`)

#### Purpose

- Use for: Call-to-action sections (often closing, but can appear anywhere)
- Can appear multiple times if user has multiple CTA sections

#### Section fields

- `eyebrow`
- `title`
- `description`
- `ctas`
- `smallprint`

#### CTA section example

```markdown
[eyebrow]: Ready to launch

## Build your next B2B campaign page today

Start with AI-assisted structure, refine messaging, and publish in minutes.

[Create my page](https://example.com/signup)
[Talk to sales](https://example.com/demo)

[smallprint]: Free trial available.
```

### 9) Custom (`type: 'custom'`)

#### Purpose

- Use for: Free-form prose content without clear structure
- Examples: "About us", "Our story", Company background, Mission statement, Brand narrative
- Only use when content is narrative prose that doesn't fit other structured types
- Do not use for content that has subtitle + description pairs (use collection instead)
- Parse headings as h2/h3 based on hierarchy, paragraphs as text
- Preserve paragraph breaks - each paragraph becomes a separate text item

#### Item types

- `eyebrow`
- `h1`, `h2`, `h3`
- `text`
- `cta`
- `image` (`imageUrl`, `imageAlt`)
- `embed` (`embedCode`)

#### Custom section example

````markdown
[eyebrow]: Our approach

# Build momentum, not bottlenecks

## Why we built LandingRabbit

### A faster path from idea to live campaign

LandingRabbit is for B2B teams that need fast launches and consistent conversion-focused copy.

[Read customer stories](https://example.com/customers)

![Editor screenshot](https://example.com/editor.webp)

```html
<iframe src="https://www.youtube.com/embed/abc123xyz" frameborder="0" allowfullscreen></iframe>
```
````

### 10) TrustedBy (`type: 'trustedBy'`)

#### Purpose

Add social-proof credibility with logos and supporting text.

#### Item types

- `eyebrow`
- `h2`, `h3`
- `text`
- `cta`
- `logos`

#### TrustedBy section example

- Use for: Sections mentioning customer/client logos or social proof logos
- Examples: "Trusted by", "Customer logos", "Client logos", "Join 5,000+ businesses", "[Logos]", "Partners"

```markdown
[eyebrow]: Social proof

## Trusted by modern B2B teams

Used by SaaS, fintech, and agencies running high-velocity campaigns.

Logos: [Add 6-10 customer logos in editor]

[See customer stories](https://example.com/customers)
```

# Example answers

- Provide as a single txt or markdown file the user can copy and paste to LandingRabbit

## Example document A

Section type: `hero`

- `suggestedLayout`: `vertical`

```markdown
[eyebrow]: B2B Website Builder

# Turn your ideas into marketing pages in 10 minutes

✅ Create landing pages in minutes
✅ Turn existing materials into publish-ready drafts
✅ Keep messaging consistent across teams

[Start your 14-day free trial](/signup)
[Book demo](/demo)

[smallprint]: No credit card needed.
```

Section type: `steps`

- `stepDecoration`: `destructive`

```markdown
[eyebrow]: Problem

## You know you need new pages, but content creation keeps dropping down your list

- Creating new pages is slow and repetitive.
- Higher-priority tasks always win.
- Updates feel risky and inconsistent.
```

Section type: `collection`

- `suggestedLayout`: `alternate`

```markdown
[eyebrow]: How it works

## LandingRabbit creates marketing pages from ideas and materials you already have

[eyebrow]: STEP 1

### Add your website URL

LandingRabbit learns your brand and business context.

![Add your website URL](https://example.com/step1.webp)

[eyebrow]: STEP 2

### Create pages from ideas and materials

Turn page ideas, sales decks, and docs into drafts.

![Create pages from ideas](https://example.com/step2.webp)
```

Section type: `comparison`

```markdown
[eyebrow]: Before vs after

## Replace fragmented workflows

A side-by-side view of your workflow shift.

[See migration guide](/migration)

### Legacy process

- ❌ Copy in one tool, design in another
- ❌ Slow handoffs
- ❌ Late launches

### LandingRabbit workflow

- ✅ One workflow from brief to publish
- ✅ Faster iteration
- ✅ Better consistency
```

Section type: `faq`

```markdown
## Frequently Asked Questions

### Can I use my own domain?

Yes, custom domains are supported.

### Can I export to other tools?

Yes. Export to Webflow, Figma, JSON, Markdown, PDF, and PNG.
```

Section type: `cta`

- `suggestedLayout`: `default`

```markdown
[eyebrow]: Ready to launch

## Create new pages from ideas you already have

Sign up and create unlimited pages.

[Start your 14-day free trial](/signup)
[Talk to sales](/demo)

[smallprint]: Free trial available.
```

## Example document B

Section type: `hero`

- `suggestedLayout`: `vertical`

```markdown
[eyebrow]: Security operations

# Reduce alert fatigue with AI-assisted triage

Help analysts focus on real threats with smarter prioritization.

[Start trial](https://security.example.com/start)
[Request demo](https://security.example.com/demo)

[smallprint]: Deploy in days, not months.
```

Section type: `collection`

- `suggestedLayout`: `alternate`

```markdown
[eyebrow]: Product value

## What your SOC gains immediately

[eyebrow]: Signal quality

### Fewer false positives

Improve triage confidence by prioritizing actionable threats.

[eyebrow]: Analyst efficiency

### Faster investigations

Automate repetitive classification and enrichment tasks.
```

Section type: `comparison`

```markdown
[eyebrow]: Current vs improved

## SOC workflow transformation

A side-by-side view of your workflow shift.

[See architecture](https://security.example.com/architecture)

### Before

- ❌ Noisy queues
- ❌ Slow context gathering
- ❌ Inconsistent prioritization

### After

- ✅ Cleaner queues
- ✅ Faster context
- ✅ Better prioritization
```

Section type: `testimonials`

- `suggestedLayout`: `grid`

```markdown
## What customers say

"We cut campaign page production from two weeks to one day.”
Maya Chen
Growth Lead
Northbeam AI

“Publishing became a same-day workflow for our team.”
Jonas Ranta
Demand Gen Manager
ScaleForge
```

Section type: `cta`

- `suggestedLayout`: `default`

```markdown
[eyebrow]: Next step

## See how your SOC can triage faster

[Book technical demo](https://security.example.com/demo)

[smallprint]: Includes architecture review.
```

## Example document C

Section type: `hero`

- `suggestedLayout`: `vertical`

```markdown
[eyebrow]: HR and People Ops

# Onboard new hires with confidence and consistency

Create role-specific onboarding journeys that improve ramp time.

[Get started](https://hr.example.com/start)
[See product tour](https://hr.example.com/tour)

[smallprint]: Trusted by distributed teams.
```

Section type: `steps`

- `stepDecoration`: `number`

```markdown
[eyebrow]: Onboarding flow

## A structured path from offer to productivity

1. Trigger onboarding when offer is accepted.
2. Assign role-based learning paths.
3. Track completion and manager checkpoints.
4. Measure 30/60/90-day ramp progress.
```

Section type: `pricing`

```markdown
[eyebrow]: Pricing

## Plans for growing teams

[Compare all plans](https://hr.example.com/pricing)

[eyebrow]: Small organizations

### Team

$199/month

Up to 100 employees

✅ Core onboarding workflows
✅ Templates and checklists
✅ Reporting dashboard

[Start Team](https://hr.example.com/start)

[eyebrow]: Scaling organizations

### Business

$499/month

Up to 500 employees

✅ Advanced automation
✅ Department reporting
✅ Priority support

[Start Business](https://hr.example.com/start)
```

Section type: `trustedBy`

```markdown
[eyebrow]: Trusted by people-first companies

## Customer proof

Used by people and talent teams scaling onboarding programs.

Logos: [Add customer logos]

[See customer stories](https://hr.example.com/customers)
```

Section type: `cta`

- `suggestedLayout`: `default`

```markdown
[eyebrow]: Ready to improve ramp time

## Start your onboarding transformation

[Book onboarding consult](https://hr.example.com/demo)

[smallprint]: Includes implementation planning session.
```

---

## Example document D

Section type: `hero`

- `suggestedLayout`: `vertical`

```markdown
[eyebrow]: Made for B2B Marketers

# Turn ideas into live pages

You know your audience. You have decks, docs, and ideas — but no time to turn them into pages.

LandingRabbit takes what you already have and **builds your pages for you**.

[Try it free for 14 days](/signup)

![LandingRabbit editor](https://d2txn9w4uujjus.cloudfront.net/images/019514e0-fe0a-7a1b-8ec6-a585eaf24e4d/f4ca041a4e31d86a77328544c6e61017a85e95e5.webp)

[smallprint]: No credit card required. Trusted by 200+ teams.
```

---

Section type: `steps`

- `stepDecoration`: `destructive`

```markdown
## You keep putting off new pages because the process is too slow

- There's **never enough time** to write and publish new content
- **Your current tools make it harder**, not easier, to ship pages fast
- And **things break** every time you try to change something live
```

---

Section type: `collection`

- `suggestedLayout`: `alternate`

```markdown
[eyebrow]: How it works

## Go from a rough idea to a live page in under 10 minutes

[eyebrow]: STEP 1

### Your brand is set up automatically

Connect your website and LandingRabbit picks up your colours, fonts, and tone — so every page looks right from day one.

![](https://d2txn9w4uujjus.cloudfront.net/images/019514e0-fe0a-7a1b-8ec6-a585eaf24e4d/0aff4ad07e81ad3025d3da21a7da9b31cdb0a27e.webp)

[eyebrow]: STEP 2

### Add your content and let AI do the heavy lifting

Drop in a keyword, a deck, or a brief — anything works. LandingRabbit turns it into a full page draft ready to publish.

![Page brief for a project management tool targeting startups](https://d2txn9w4uujjus.cloudfront.net/images/019514e0-fe0a-7a1b-8ec6-a585eaf24e4d/3e0f32ed19037413965b6515d316402032b113c9.webp)

[eyebrow]: STEP 3

### Fine-tune your draft with a live preview alongside

AI handles the first draft — you polish the rest. Ask LandingRabbit to tweak copy or adjust the design at any point.

![](https://d2txn9w4uujjus.cloudfront.net/images/019514e0-fe0a-7a1b-8ec6-a585eaf24e4d/e5bad939dbabfb5778b12a88b14958f7ff87c3be.webp)

[eyebrow]: STEP 4

### Publish to your own domain in minutes

Skip the pixel-pushing. Hit publish on mycompany.com and start sharing with prospects right away.

![Three LandingRabbit-powered websites showcasing B2B services](https://d2txn9w4uujjus.cloudfront.net/images/019514e0-fe0a-7a1b-8ec6-a585eaf24e4d/14004194a24aa9d51e274ece2d00fe6da2cd170c.webp)
```

---

Section type: `collection`

- `suggestedLayout`: `boxes`

```markdown
## Build more pages from what you already know

Your best content is already in your tools. Use it to make pages that convert. 👇

### Keywords into ad and SEO pages

Feed in your keyword list and get Google Ads-ready landing pages. More clicks, same budget.

![](https://d2txn9w4uujjus.cloudfront.net/images/019514e0-fe0a-7a1b-8ec6-a585eaf24e4d/63a990a04927d379d08e4bbad650687cea98075c.webp)

### Product specs into solution pages

Turn internal docs and specs into polished solution pages and help content. Put your work in front of buyers.

![](https://d2txn9w4uujjus.cloudfront.net/images/019514e0-fe0a-7a1b-8ec6-a585eaf24e4d/c8743e062428084c2ea0ccdfe784bd5c1193e973.webp)

### Slides into role and industry pages

Repurpose your pitch decks into role-specific or industry-specific pages that speak directly to each visitor.

![](https://d2txn9w4uujjus.cloudfront.net/images/019514e0-fe0a-7a1b-8ec6-a585eaf24e4d/48e15bcd4865933e211575de36259fc768d0ace8.webp)

### Sales notes into account pages

Convert your call notes into personalised ABM pages. Show each prospect you understand their problem.

![](https://d2txn9w4uujjus.cloudfront.net/images/019514e0-fe0a-7a1b-8ec6-a585eaf24e4d/4ae7b830ceb6c0cdf4d96491b55c488392a9f195.webp)

### Blog posts into use case pages

Repurpose your best posts into dedicated use case pages. Capture leads you'd otherwise lose.

![](https://d2txn9w4uujjus.cloudfront.net/images/019514e0-fe0a-7a1b-8ec6-a585eaf24e4d/75c44076465cf410fa1475ef49b983ff8988f519.webp)

### Research into comparison pages

Take your competitive research and turn it into comparison pages that make the choice obvious for buyers.

![](https://d2txn9w4uujjus.cloudfront.net/images/019514e0-fe0a-7a1b-8ec6-a585eaf24e4d/c46dea6f2d172fdba36b8211eef7a2de2704e72e.webp)
```

---

Section type: `custom`

- `suggestedLayout`: `middle`

````markdown
## See it in action — your first page in under five minutes 👇

```html
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/LJBWYbja7R0?si=bipThkyW5-AEOfpr"
  title="YouTube video player"
  frameborder="0"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
  allowfullscreen
></iframe>
```
````

---

Section type: `faq`

```markdown
## Common questions

### What makes LandingRabbit different?

Most page builders make you start from a blank canvas. LandingRabbit starts from what you already have — decks, notes, keywords, or any other content you own.

### How do I get started?

[Start your free trial](/signup) and have your first page live before the end of the day.

### Where can I publish my pages?

Publish straight to your own domain (e.g., mycompany.com), or export into [Figma](/figma-plugin) and drop it into any custom site.

### Can my team review pages before they go live?

Absolutely. Invite teammates to collaborate inside LandingRabbit, or share a private preview link to collect feedback before you hit publish.

### What if I'm stuck on the copy?

Just ask. LandingRabbit knows your business and your materials, so it can rewrite sections, suggest alternatives, or rework the whole page — whenever you need a hand.

### What does it cost?

Plans start at $39/month. Find all the details on [our pricing page](/pricing).

### Can I use LandingRabbit as my main website?

Yes — use a subdomain for campaign pages or point your whole domain to LandingRabbit.
```

---

Section type: `cta`

- `suggestedLayout`: `embed`

````markdown
## Start shipping pages today

Join 200+ teams and in your first 14 days:

✅ **Unlimited pages** — ads, help docs, blog posts, and anything else you need
✅ **Team reviews built in** — share drafts and collect feedback before you publish
✅ **Your domain, your rules** — publish on your own URL or export to Figma and custom sites
✅ **Direct access to the founders** — people who've built websites for 15+ years

```html
<style>
  .signup-form {
    width: 320px;
    padding: 25px;
    border-radius: 8px;
    background: #ffffff;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    font-family: Arial, sans-serif;
  }

  .signup-form h2 {
    text-align: center;
    margin-bottom: 20px;
  }

  .signup-form label {
    display: block;
    margin-bottom: 5px;
    font-size: 14px;
  }

  .signup-form input {
    width: 100%;
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 14px;
  }

  .signup-form input:focus {
    outline: none;
    border-color: #4caf50;
  }

  .signup-form button {
    width: 100%;
    padding: 10px;
    background: #4caf50;
    color: white;
    border: none;
    border-radius: 5px;
    font-size: 16px;
    cursor: pointer;
  }

  .signup-form button:hover {
    background: #43a047;
  }
</style>

<div class="signup-form">
  <h2>Sign Up</h2>
  <form>
    <label>Name</label>
    <input type="text" placeholder="Enter your name" required />

    <label>Email Address</label>
    <input type="email" placeholder="Enter your email" required />

    <label>Password</label>
    <input type="password" placeholder="Enter password" required />

    <button type="submit">Sign Up</button>
  </form>
</div>
```
````
