# Claude Code Starter

## What This Is

A pre-configured Claude Code project with **20 skills** covering voice/audio, strategic analysis, opportunity evaluation, and product development.

## How to Use Skills

Just ask naturally. Claude will automatically pick the right skill:

| What You Want | What to Say |
|--------------|-------------|
| Transcribe a recording | "Transcribe this meeting recording" |
| Get an audio briefing | "Turn this transcript into an audio briefing" |
| Analyse a meeting | "Analyse this transcript and give me the strategic takeaways" |
| Evaluate a new idea | "I have a business idea — help me evaluate it" |
| Research a market | "How big is the [X] market?" |
| Map competitors | "Who are the main players in [market]?" |
| Score an opportunity | "Score this opportunity — should I pursue it?" |
| Start a product build | "Help me write a PRD for [product]" |

You can also type a slash command directly, like `/voice-to-text` or `/opportunity-brief`.

---

## All Skills

### Voice & Audio
| Skill | What It Does |
|-------|-------------|
| `/voice-to-text` | Transcribe audio/video files to text with speaker identification |
| `/text-to-voice` | Convert any text file to MP3 using local TTS (Kokoro, Orpheus, or Coqui XTTS v2) |
| `/voice-briefing` | Turn a meeting transcript or document into a spoken audio briefing |

### Strategic Analysis
| Skill | What It Does |
|-------|-------------|
| `/strategic-analysis` | Analyse meetings or documents with full project context awareness |
| `/competitive-intel` | Competitive gap analysis — signal vs noise classification, gap matrix, actionable report |

### Opportunity Evaluation
| Skill | What It Does |
|-------|-------------|
| `/opportunity-brief` | Capture and document a new business opportunity |
| `/market-research` | Size the market, find demand signals, check trends |
| `/competitor-landscape` | Map existing players in a market to assess room for entry |
| `/strategy-session` | Brainstorm go-to-market, differentiation, blue ocean thinking |
| `/due-diligence` | Vet people, financials, legal, and technical feasibility |
| `/viability-assessment` | Score the opportunity across 8 dimensions and make the call |

### Product Development (BMAD)
| Skill | What It Does |
|-------|-------------|
| `/bmad` | Structured product development with specialised AI agents (analyst, PM, architect, designer, developer, scrum master) |

---

## Commands

| Command | What It Does |
|---------|-------------|
| `/new-idea` | Scaffold a new idea directory with all the right files |

---

## Evaluating a New Idea

The opportunity evaluation skills work as a pipeline:

1. `/new-idea` — Scaffold a directory for the idea
2. `/opportunity-brief` — Capture what you know: pitch, model, people, risks
3. `/market-research` — Size the market, find demand signals, check trends
4. `/competitor-landscape` — Map existing players, find gaps
5. `/strategy-session` — Brainstorm go-to-market, differentiation
6. `/due-diligence` — Vet people, financials, legal, technical feasibility
7. `/viability-assessment` — Score the opportunity and make the call

---

## Tips for Best Results

### Be Specific
- Bad: "Analyse this"
- Good: "Analyse this meeting transcript and focus on competitive threats and action items for the engineering team"

### Give It Context
- Share URLs and let Claude read them
- Paste in documents you want analysed
- Share competitor URLs for landscape mapping

### Use Web Search
Claude can search the web in real-time:
- "Search for [competitor] and analyse their positioning"
- "What are people on Reddit saying about [topic]?"
- "Find the latest stats on [industry trend]"

---

## File Structure

```
claude-code-starter/
├── .claude/
│   ├── CLAUDE.md                  ← This file (project instructions)
│   ├── commands/                  ← Slash commands
│   └── skills/                    ← All skills
│       ├── voice-to-text/
│       ├── text-to-voice/
│       ├── voice-briefing/
│       ├── strategic-analysis/
│       ├── competitive-intel/
│       ├── opportunity-brief/
│       ├── market-research/
│       ├── competitor-landscape/
│       ├── strategy-session/
│       ├── due-diligence/
│       ├── viability-assessment/
│       └── bmad/
└── guide.html                     ← Getting started guide
```

## Notes

- Skills are markdown files that teach Claude how to approach specific tasks
- You can edit any skill file to customise how Claude works for your needs
- Add more skills from [skills.sh](https://skills.sh/) or create your own
