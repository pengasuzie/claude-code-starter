# Claude Code Marketing Kit

## What This Is

This is your AI-powered marketing toolkit. It contains **42 skills** that make Claude Code think like a marketing professional — covering strategy, copywriting, SEO, conversion optimisation, analytics, and more.

## How to Use Skills

Just ask naturally. Claude will automatically pick the right skill:

| What You Want | What to Say |
|--------------|-------------|
| Plan what content to create | "What should we blog about for [client]?" |
| Write a blog post or landing page | "Write a landing page for [product]" |
| Improve a page's conversions | "How can we improve this page's conversion rate?" |
| Audit a site's SEO | "Run an SEO audit on [website]" |
| Add structured data for Google | "Add schema markup to this page" |
| Research competitors | "Analyse our competitors for [client]" |
| Document a new client | "Set up a brief for [client name]" |
| Create an email sequence | "Build a welcome email sequence for [product]" |
| Plan a product launch | "Help me plan the launch for [feature]" |
| Set up A/B testing | "Design an A/B test for our pricing page" |
| Optimise signup flow | "How can we reduce signup drop-off?" |
| Create social content | "Write LinkedIn posts for this week" |
| Set up analytics tracking | "Help me set up GA4 event tracking" |

You can also type a slash command directly, like `/copywriting` or `/seo-audit`.

---

## All Skills

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

---

## The Client Brief System

The **Client Brief** is the foundation. Set up a client once, and every other skill automatically knows the context.

1. Run `/client-brief` and answer the questions about the client
2. It creates a `product-marketing-context.md` file
3. **All other skills read this file** before giving advice — no need to repeat yourself

### Multiple Clients

- Each client gets their own context file in `.claude/clients/`
- Switch clients by telling Claude "I'm working on [client name]" and it will find the right brief

---

## Slash Commands

| Command | What It Does |
|---------|-------------|
| `/commit` | Analyse your changes and create a clean git commit |

---

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

---

## Tips for Best Results

### Be Specific
- Bad: "Write a blog post about marketing"
- Good: "Write a 1,200-word blog post for [client]'s audience of CFOs about why fractional CMOs outperform agencies, in a confident but not arrogant tone"

### Give It Context
- Share the client's website URL and let Claude read it
- Paste in existing copy you want improved
- Share competitor URLs for analysis

### Iterate
- "Make the headline punchier"
- "This is too formal, make it more conversational"
- "Add more specific examples"
- "Shorten this by 30%"

### Use Web Search
Claude can search the web in real-time:
- "Search for [competitor] and analyse their positioning"
- "What are people on Reddit saying about [topic]?"
- "Find the latest stats on [industry trend]"

---

## File Structure

```
claude-code-marketing-kit/
├── .claude/
│   ├── CLAUDE.md                     ← This file (project instructions)
│   ├── product-marketing-context.md  ← Active client brief
│   ├── clients/                      ← Client briefs (one per client)
│   ├── commands/                     ← Slash commands
│   └── skills/                       ← All 42 marketing skills
│       ├── client-brief/
│       ├── competitor-analysis/
│       ├── content-strategy/
│       ├── copywriting/
│       ├── seo-audit/
│       ├── page-cro/
│       └── ... (36 more)
└── guide.html                        ← Getting started guide
```

## Notes

- Skills are markdown files that teach Claude how to approach specific marketing tasks
- The `product-marketing-context.md` file is the glue that connects all skills to your current client
- You can edit any skill file to customise how Claude works for your needs
