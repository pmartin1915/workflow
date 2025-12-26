# Claude Multi-Model Workflow

A structured workflow system for maximizing productivity with Claude (Opus/Sonnet) + Gemini via PAL MCP.

## Overview

This workflow enables:
- **Opus** for architecture, planning, and complex decisions
- **Sonnet** for implementation and routine coding
- **Gemini 3 Pro** for code review and outside perspectives (1M context)
- **Gemini Flash** for quick iterations and fallback

## Quick Start

1. Copy the appropriate template from `templates/` for your project
2. Customize the project context section
3. Paste at the start of each Claude session

## Repository Structure

```
workflow/
├── README.md                    # This file
├── templates/
│   ├── WORKFLOW-TEMPLATE.md     # Generic template for any project
│   ├── healthcare-apps.md       # Healthcare education apps template
│   └── land-auction.md          # Land auction app template
├── pal-mcp/
│   ├── PAL-MCP-SETUP.md         # PAL MCP troubleshooting guide
│   ├── CREATE-GEMINI-KEY.md     # How to create Gemini API keys
│   └── Switch-GeminiKey.ps1     # One-command key switcher
└── docs/
    └── model-selection.md       # Model selection rationale
```

## PAL MCP Setup

PAL MCP server location: `C:\Users\perry\pal-mcp-server`

Key files:
- `.env` - API keys (with `PAL_MCP_FORCE_ENV_OVERRIDE=true`)
- `mcp.json` - Claude Code config at `%APPDATA%\Code\User\mcp.json`
- `gemini-keys.json` - Backup API keys (not in this repo for security)

## Gemini API Keys

You have ~$900 in Gemini credits across 3 accounts. When one runs out:

```powershell
cd C:\Users\perry\pal-mcp-server
.\Switch-GeminiKey.ps1 -ApiKey "AIzaNewKey" -ProjectNumber "123456"
# Restart VSCode
```

## Model Selection Guide

| Model | Cost | Use For |
|-------|------|---------|
| Opus | $$$ | Planning, architecture, complex debugging |
| Sonnet | $$ | Implementation, refactoring, routine tasks |
| Gemini 3 Pro | Free* | Code review, large files, second opinions |
| Gemini Flash | Free* | Quick iterations, fallback |

*Uses $300 free credit per Google account

## Session Management

- Keep plans within **40-70% of context window**
- One focused feature per session
- Use TodoWrite for multi-step tasks
- Summarize at session end for handoff

## License

Personal use - Perry Martin
