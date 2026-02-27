# Claude Code Marketing Kit

42 marketing skills for Claude Code — strategy, copywriting, SEO, CRO, analytics, and more.

Describe your client once. Every skill remembers the context. No repeating yourself.

## Quick Start

### 1. Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

You'll need an Anthropic API key. Get one at [console.anthropic.com](https://console.anthropic.com)

### 2. Open This Project

```bash
cd claude-code-marketing-kit
claude
```

Claude Code automatically detects the `.claude/` folder and loads all 42 skills.

### 3. Try It Out

```
> Set up a client brief for [client name]
> Run an SEO audit on example.com
> What content should we create for [client]?
> Write a LinkedIn post about why fractional marketing works
> Analyse the competitors for [client]
```

## How It Works

### The Client Brief System

The **Client Brief** is the foundation. Set up a client once, and every skill automatically knows the context.

1. Run `/client-brief` and answer the questions about the client
2. It creates a `product-marketing-context.md` file
3. **All other skills read this file** before giving advice — no need to repeat yourself

### Multiple Clients

Each client gets their own context file in `.claude/clients/`. Switch clients by telling Claude "I'm working on [client name]" and it loads the right brief.

## All 42 Skills

### Foundation & Strategy

| Skill | What It Does |
|-------|-------------|
| `/client-brief` | Document a client's brand, audience, and marketing context — the foundation all other skills read |
| `/product-marketing-context` | Create or update the shared product marketing context document |
| `/competitor-analysis` | Research and benchmark against competitors to find positioning opportunities |
| `/marketing-ideas` | Generate ideas from a library of 139 proven marketing approaches |
| `/marketing-psychology` | Apply psychological principles and behavioural science to marketing |
| `/pricing-strategy` | Design pricing tiers, packaging, and monetisation strategy |
| `/launch-strategy` | Plan product launches, feature announcements, and go-to-market strategies |
| `/referral-program` | Design referral programs, affiliate programs, and word-of-mouth loops |
| `/free-tool-strategy` | Plan free marketing tools (calculators, generators) for lead gen and SEO |

### Content & Copywriting

| Skill | What It Does |
|-------|-------------|
| `/content-strategy` | Plan what content to create, build topic clusters, prioritise by impact |
| `/copywriting` | Write or improve copy for any asset — blog posts, landing pages, emails, ads |
| `/copy-editing` | Review and polish existing marketing copy through systematic multi-pass editing |
| `/email-sequence` | Create email drip campaigns, welcome sequences, and lifecycle automations |
| `/social-content` | Create content for LinkedIn, Twitter/X, Instagram, TikTok, and other platforms |
| `/paid-ads` | Build paid ad campaigns on Google, Meta, LinkedIn — copy, targeting, and optimisation |

### SEO

| Skill | What It Does |
|-------|-------------|
| `/seo-audit` | Full technical + on-page SEO audit with prioritised fix list |
| `/seo-plan` | Strategic SEO planning with industry templates and implementation roadmaps |
| `/seo-page` | Deep single-page analysis — on-page elements, meta tags, schema, images, performance |
| `/seo-content` | Content quality and E-E-A-T analysis with AI citation readiness |
| `/seo-technical` | Technical SEO audit across 8 categories (crawlability, indexability, security, etc.) |
| `/seo-competitor-pages` | Generate "X vs Y" and "alternatives to X" comparison pages |
| `/seo-geo` | Optimise for AI Overviews, ChatGPT search, Perplexity, and other AI search engines |
| `/seo-hreflang` | Audit and generate hreflang tags for international/multilingual SEO |
| `/seo-images` | Optimise images for SEO — alt text, file names, compression, lazy loading |
| `/seo-programmatic` | Build programmatic SEO pages at scale from data templates |
| `/seo-schema` | Detect, validate, and generate Schema.org structured data (JSON-LD) |
| `/seo-sitemap` | Analyse existing XML sitemaps or generate new ones |
| `/programmatic-seo` | Create SEO-driven pages at scale — location pages, integrations, comparisons |
| `/schema-markup` | Add, fix, or optimise JSON-LD schema markup for rich search results |
| `/competitor-alternatives` | Build competitor comparison and alternative pages for SEO and sales enablement |

### Conversion Rate Optimisation (CRO)

| Skill | What It Does |
|-------|-------------|
| `/page-cro` | Optimise any marketing page (homepage, landing, pricing) for better conversions |
| `/signup-flow-cro` | Reduce drop-off in signup, registration, and free trial activation flows |
| `/onboarding-cro` | Improve post-signup onboarding, activation, and time-to-value |
| `/paywall-upgrade-cro` | Optimise in-app paywalls, upgrade screens, and freemium-to-paid moments |
| `/form-cro` | Improve completion rates on lead capture, contact, and demo request forms |
| `/popup-cro` | Create and optimise popups, modals, exit-intent overlays, and banners |
| `/ab-test-setup` | Design statistically valid A/B tests with clear hypotheses and success metrics |

### Analytics & Measurement

| Skill | What It Does |
|-------|-------------|
| `/analytics-tracking` | Set up and audit GA4, GTM, event tracking, UTM parameters, and tracking plans |

### Voice & Audio

| Skill | What It Does |
|-------|-------------|
| `/voice-to-text` | Transcribe audio/video files to text with speaker identification |
| `/voice-briefing` | Turn a meeting transcript or document into a spoken audio briefing |

### Utility

| Skill | What It Does |
|-------|-------------|
| `/find-skills` | Search for available skills when you want to extend capabilities |
| `/bmad` | BMAD Method for structured product development workflows |

## Recommended Workflow for a New Client

1. **Document** — `/client-brief` to capture who they are, what they do, who they serve
2. **Research** — `/competitor-analysis` to understand the competitive landscape
3. **Audit** — `/seo-audit` to diagnose their current website
4. **Plan** — `/content-strategy` to decide what content to create
5. **Write** — `/copywriting` to produce the actual content
6. **Optimise** — `/page-cro` to improve conversions on key pages
7. **Enhance** — `/schema-markup` to add structured data for better search visibility
8. **Measure** — `/analytics-tracking` to set up proper tracking
9. **Launch** — `/launch-strategy` when you're ready to go live
10. **Grow** — `/email-sequence`, `/social-content`, `/paid-ads` to drive traffic

## Useful Claude Code Basics

| What | How |
|------|-----|
| Start Claude Code | `claude` (in terminal) |
| Use a skill | Just ask naturally, or type `/skill-name` |
| Clear conversation | `/clear` |
| Compact conversation | `/compact` (frees memory without losing context) |
| Get help | `/help` |
| Exit | `/exit` or Ctrl+C |

## Customising

- **Edit a skill**: Open `.claude/skills/[name]/SKILL.md` in any text editor
- **Add a new skill**: Create a new folder in `.claude/skills/` with a `SKILL.md` file
- **Edit project instructions**: Open `.claude/CLAUDE.md`
- **Add a command**: Create a new `.md` file in `.claude/commands/`

## Permissions

The kit ships with a `settings.local.json` that pre-approves common tools (file editing, web search, bash). It also includes permissions for Google Search Console and GA4 MCP servers — if you have those set up, they work automatically with the SEO and analytics skills.

## Optional Add-on Skills

This kit focuses on marketing. If you also want development skills (Cloudflare Workers, Vercel, accessibility auditing, web performance, etc.), you can install them from the open skills ecosystem:

```
npx skills find cloudflare
npx skills find vercel
npx skills find accessibility
```

Browse available skills at [skills.sh](https://skills.sh/)

## File Structure

```
claude-code-marketing-kit/
├── README.md                          ← You are here
├── guide.html                         ← Interactive getting started guide
├── .claude/
│   ├── CLAUDE.md                      ← Project instructions (Claude reads this automatically)
│   ├── settings.local.json            ← Permissions and configuration
│   ├── product-marketing-context.md   ← Active client brief (created by /client-brief)
│   ├── clients/                       ← Client briefs (one per client)
│   ├── commands/
│   │   └── bmad/                      ← BMAD product development commands
│   └── skills/                        ← All 42 marketing skills
│       ├── client-brief/
│       ├── copywriting/
│       ├── seo-audit/
│       ├── page-cro/
│       └── ... (38 more)
```

## Need Help?

- Claude Code docs: https://docs.anthropic.com/en/docs/claude-code
- Report issues: https://github.com/anthropics/claude-code/issues

## Credits

This kit includes the [BMAD Method](https://github.com/bmad-code-org/BMAD-METHOD) skills and commands for structured product development workflows. BMAD is MIT licensed, copyright (c) 2025 BMad Code, LLC.

## License

MIT
