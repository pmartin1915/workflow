# Healthcare Education Apps - Session Template

Copy this prompt to start a new session:

```
## Project Context
I am working on my healthcare education applications. Current focus: [burn-wizard/clinical-toolkit/medilex].

## Multi-Model Workflow
Use this model strategy:

| Model | Role | When to Use |
|-------|------|-------------|
| **Opus** (you) | Architect | Planning, complex decisions, debugging |
| **Sonnet** | Implementer | Routine coding, refactoring |
| **Gemini 3 Pro** | Reviewer | Code review, outside perspective |
| **Gemini Flash** | Quick helper | Fast iterations, fallback |

### Calling Gemini via PAL MCP
- Code review: `mcp__pal__chat` with model="gemini-3-pro-preview"
- Quick tasks: `mcp__pal__chat` with model="gemini-2.5-flash"
- If Pro fails, retry with Flash

## Session Management
- Keep plans within **40-70% of context**
- Use TodoWrite for multi-step tasks
- Summarize at session end

## Healthcare Specifics
- Clinical accuracy is critical
- HIPAA considerations for user data
- Accessibility for clinical environments
- Mobile-responsive design

## Current Session
[Describe what you want to accomplish]

Take your time. Ask questions and give suggestions as needed.
```

## Project Locations

| App | Path |
|-----|------|
| burn-wizard | `D:\Project\healthcare-apps\burn-wizard` |
| clinical-toolkit | `D:\Project\healthcare-apps\clinical-toolkit` |
| medilex | `D:\Project\healthcare-apps\medilex` |

## Recent Handoffs

Check `D:\Project\healthcare-apps\` for:
- `HANDOFF_NEXT_SESSION.md`
- `BURN_WIZARD_EXPO_MIGRATION_PLAN.md`
- Other `*_HANDOFF*.md` files
