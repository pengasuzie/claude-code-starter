# Claude Code Starter

A pre-configured Claude Code project to get you productive fast. Includes 20 skills for voice/audio, strategic analysis, opportunity evaluation, and product development — plus an interactive getting-started guide.

## Quick Start

### 1. Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

You'll need an Anthropic API key. Get one at [console.anthropic.com](https://console.anthropic.com)

### 2. Open This Project

```bash
cd claude-code-starter
claude
```

Claude Code automatically detects the `.claude/` folder and loads all skills.

### 3. Try It Out

```
> Transcribe this meeting recording
> Analyse this transcript and give me a strategic briefing
> I have a new business idea — help me evaluate it
> Map out the competitors in [market]
> Score this opportunity — should I pursue it?
```

## Included Skills

### Voice & Audio

| Skill | What It Does |
|-------|-------------|
| `/voice-to-text` | Transcribe audio/video files to text with speaker identification |
| `/text-to-voice` | Convert any text file to MP3 using local TTS (Kokoro, Orpheus, or Coqui XTTS v2) |
| `/voice-briefing` | Turn a meeting transcript into a spoken audio briefing |

### Strategic Analysis

| Skill | What It Does |
|-------|-------------|
| `/strategic-analysis` | Analyse meetings or documents with full project context — grounded in actual capabilities and competitive landscape |
| `/competitive-intel` | Competitive gap analysis — signal vs noise classification, gap matrix, actionable report |

### Opportunity Evaluation

| Skill | What It Does |
|-------|-------------|
| `/opportunity-brief` | Capture and document a new business opportunity in a structured format |
| `/market-research` | Size the market, find demand signals, check trends |
| `/competitor-landscape` | Map existing players in a market to assess room for entry |
| `/strategy-session` | Brainstorm go-to-market, differentiation, blue ocean thinking |
| `/due-diligence` | Vet people, financials, legal, and technical feasibility |
| `/viability-assessment` | Score the opportunity across 8 dimensions and make the call |

### Product Development (BMAD)

| Skill | What It Does |
|-------|-------------|
| `/bmad` | Structured product development workflows with specialised AI agents |

BMAD includes agents for: Business Analyst, Product Manager, System Architect, UX Designer, Scrum Master, Developer, and Creative Intelligence.

### Commands

| Command | What It Does |
|---------|-------------|
| `/new-idea` | Scaffold a new idea directory with all the right files |

## Evaluating a New Idea

The opportunity evaluation skills work as a pipeline:

1. `/new-idea` — Scaffold a directory for the idea
2. `/opportunity-brief` — Capture what you know: pitch, model, people, risks
3. `/market-research` — Size the market, find demand signals, check trends
4. `/competitor-landscape` — Map existing players, find gaps
5. `/strategy-session` — Brainstorm go-to-market, differentiation
6. `/due-diligence` — Vet people, financials, legal, technical feasibility
7. `/viability-assessment` — Score the opportunity and make the call

## Adding More Skills

This is a starter — you can add any skills you need. Browse and install from the open skills ecosystem:

```
npx skills find marketing
npx skills find seo
npx skills find cloudflare
```

Browse available skills at [skills.sh](https://skills.sh/)

Or create your own: add a folder in `.claude/skills/` with a `SKILL.md` file.

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

The project ships with a `settings.local.json` that pre-approves common tools (file editing, web search, bash). It also includes permissions for Google Search Console and GA4 MCP servers — if you have those set up, they work automatically.

## File Structure

```
claude-code-starter/
├── README.md                      ← You are here
├── guide.html                     ← Interactive getting started guide
├── .claude/
│   ├── CLAUDE.md                  ← Project instructions (Claude reads this automatically)
│   ├── settings.local.json        ← Permissions and configuration
│   ├── commands/
│   │   ├── new-idea.md            ← /new-idea command
│   │   └── bmad/                  ← BMAD product development commands
│   └── skills/
│       ├── voice-to-text/         ← Audio/video transcription
│       ├── text-to-voice/         ← Text to speech
│       ├── voice-briefing/        ← Audio briefings
│       ├── strategic-analysis/    ← Meeting/document analysis
│       ├── competitive-intel/     ← Competitive gap analysis
│       ├── opportunity-brief/     ← Capture business opportunities
│       ├── market-research/       ← Market sizing and trends
│       ├── competitor-landscape/  ← Map competitors
│       ├── strategy-session/      ← Brainstorm and strategise
│       ├── due-diligence/         ← Vet opportunities
│       ├── viability-assessment/  ← Score and decide
│       └── bmad/                  ← Product development agents
```

## Need Help?

- Claude Code docs: https://docs.anthropic.com/en/docs/claude-code
- Report issues: https://github.com/anthropics/claude-code/issues

## Credits

This project includes the [BMAD Method](https://github.com/bmad-code-org/BMAD-METHOD) for structured product development workflows. BMAD is MIT licensed, copyright (c) 2025 BMad Code, LLC.

## License

MIT
