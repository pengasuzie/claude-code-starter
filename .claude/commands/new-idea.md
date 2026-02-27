---
name: new-idea
description: Scaffold a new idea directory with all the right files
---

# New Idea

Capture a new idea while the context is fresh.

## Instructions

1. **Ask "What's the idea?"**
   > "What's the idea? Just dump what you're thinking — a sentence, a paragraph, a link. I'll sort it out."

   **STOP and wait.**

2. **Extract a slug and one-liner from their response**
   - Derive a short kebab-case slug for the directory name (e.g., `book-to-audio`, `freight-ai-marketplace`)
   - Write a one-liner summary of the idea
   - If anything is unclear, confirm the name before creating. Otherwise just go.

3. **Scan conversation for context**
   Look back through the current conversation for anything relevant to this idea:
   - Links discussed (repos, articles, competitor sites)
   - Technical details or constraints mentioned
   - Inspiration or prior art referenced
   - Problems or opportunities identified

   Capture this as `notes/initial-context.md` — a raw dump of everything relevant from the conversation, with sources.

4. **Create the directory structure**
   ```
   ideas/[idea-name]/
   ├── README.md              ← Overview, status, gut-check
   ├── notes/
   │   └── initial-context.md ← Auto-captured from conversation
   ├── research/              ← Market research outputs
   ├── competitors/           ← Competitor profiles and analysis
   ├── docs/                  ← Uploaded documents, pitch decks, financials
   └── notes/                 ← Meeting notes, strategy session outputs
   ```

5. **Create README.md** with this template:
   ```markdown
   # [Idea Name]

   **Status**: Evaluating
   **Created**: [date]
   **Tags**: [suggest 2-3 tags like #saas, #side-project, #tool, #content, #marketplace, #ai, #b2b, #b2c, #dev-tool]
   **Go/No-Go**: Pending

   ## One-liner
   [One sentence summary derived from their description]

   ## Why this is interesting
   - [Bullet 1]
   - [Bullet 2]

   ## What could kill it
   - [Bullet 1]
   - [Bullet 2]

   ## Key Links
   | Resource | URL |
   |----------|-----|
   | [any links from conversation] | |

   ## Key People
   | Name | Role | Notes |
   |------|------|-------|
   | | | |

   ## Evaluation Progress
   - [ ] Opportunity brief captured
   - [ ] Market research complete
   - [ ] Competitor landscape mapped
   - [ ] Strategy session done
   - [ ] Due diligence complete
   - [ ] Viability assessment scored
   - [ ] Go/No-Go decision made

   ## Decision Log
   | Date | Decision | Rationale |
   |------|----------|-----------|
   | | | |
   ```

   Fill in the one-liner and key links from conversation context.

6. **Ask for the gut-check**
   > "I've pre-filled what I could from our conversation. Two quick questions:
   >
   > **Why is this interesting?** What's the bet — why could this work?
   >
   > **What could kill it?** What's the biggest risk or reason this doesn't work?"

   **STOP and wait.** Fill in the gut-check sections with their answers.

7. **Set this as the active idea**
   Create/update `.claude/active-opportunity.md`:
   ```markdown
   # Active Idea
   Currently evaluating: [Idea Name]
   Path: ideas/[idea-name]/
   ```

8. **Suggest next step**
   > "You're set up. Next steps when you're ready:
   >
   > - `/opportunity-brief` — flesh out the full picture (model, people, risks)
   > - `/market-research` — size the market and find demand signals
   > - `/competitor-landscape` — see who else is playing here
   >
   > Or just keep chatting about it — I'll remember the context."
