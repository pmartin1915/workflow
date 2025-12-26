# Alabama Auction Watcher - Session Template

Copy this prompt to start a new session:

```
## Project Context
I am working on the Alabama land auction application. Current focus: [feature/component].

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

## Land Auction Specifics
- Data scraping reliability and error handling
- Real-time notification accuracy
- User authentication and saved searches
- Map/GIS integration
- Alabama-specific auction data sources

## Current Session
[Describe what you want to accomplish]

Take your time. Ask questions and give suggestions as needed.
```

## Project Location

`C:\Users\perry\Alabama Auction Watcher\`

```
├── Application/     # Frontend
├── Backend/         # API and scraping
├── Config/          # Configuration
├── Icons/           # App icons
└── Logs/            # Logs
```
