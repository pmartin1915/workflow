# Model Selection Rationale

## The Multi-Model Strategy

Using multiple AI models strategically maximizes productivity and cost-effectiveness.

## Model Breakdown

### Claude Opus (Primary)
- **Cost**: Highest
- **Strengths**: Deep reasoning, nuanced decisions, complex architecture
- **Use For**:
  - Initial planning and architecture
  - Complex debugging
  - Quality gates and final reviews
  - Critical decision-making
- **Preserve For**: High-value tasks that need the best reasoning

### Claude Sonnet (Secondary)
- **Cost**: Medium
- **Strengths**: Fast, excellent coding, good reasoning
- **Use For**:
  - Implementation of planned features
  - Refactoring
  - Routine coding tasks
  - Simple bug fixes
- **When to Switch**: For straightforward implementation after Opus plans

### Gemini 3 Pro (via PAL MCP)
- **Cost**: Free ($300 credit per account, ~$900 total)
- **Strengths**: 1M token context, different perspective
- **Use For**:
  - Code review (catches things Claude might miss)
  - Second opinions on architecture
  - Processing large files
  - Security/performance analysis
- **How to Call**: `mcp__pal__chat` with `model="gemini-3-pro-preview"`

### Gemini Flash (via PAL MCP)
- **Cost**: Free (same credit pool)
- **Strengths**: Ultra-fast, 1M context
- **Use For**:
  - Quick iterations
  - Simple queries
  - Fallback when Pro is unavailable
  - Preserving Claude context for complex work
- **How to Call**: `mcp__pal__chat` with `model="gemini-2.5-flash"`

## Typical Session Flow

```
┌─────────────────────────────────────────────────────────┐
│  1. PLANNING (Opus)                                     │
│     └── Read requirements, create implementation plan   │
├─────────────────────────────────────────────────────────┤
│  2. REVIEW PLAN (Gemini 3 Pro - Optional)              │
│     └── Get outside perspective on approach             │
├─────────────────────────────────────────────────────────┤
│  3. IMPLEMENTATION (Opus or Sonnet)                    │
│     └── Write the code                                  │
├─────────────────────────────────────────────────────────┤
│  4. CODE REVIEW (Gemini 3 Pro)                         │
│     └── Check for issues, security, performance         │
├─────────────────────────────────────────────────────────┤
│  5. FIXES & POLISH (Opus)                              │
│     └── Address review feedback, handle edge cases      │
├─────────────────────────────────────────────────────────┤
│  6. WRAP UP (Opus)                                     │
│     └── Summarize, create handoff if needed             │
└─────────────────────────────────────────────────────────┘
```

## Cost Optimization

### Maximizing Claude Max Value
1. Use Gemini for reviews (free) instead of Claude
2. Delegate simple tasks to Gemini Flash
3. Save Opus for planning and complex decisions
4. Consider Sonnet for implementation phases

### Maximizing Gemini Credit
1. Use Flash for simple tasks (cheaper)
2. Use Pro only when you need deep analysis
3. Switch accounts when credit runs low
4. Monitor usage at aistudio.google.com

## Fallback Strategy

If Gemini 3 Pro fails (quota, overload, etc.):
1. Retry with Gemini Flash
2. If all Gemini fails, continue with Claude
3. If credit exhausted, switch API key and restart VSCode

## When to Use Each Model

| Task | Best Model | Fallback |
|------|------------|----------|
| Architecture planning | Opus | - |
| Complex debugging | Opus | Gemini Pro |
| Code implementation | Sonnet/Opus | - |
| Code review | Gemini Pro | Gemini Flash |
| Quick questions | Gemini Flash | - |
| Large file analysis | Gemini Pro | - |
| Security audit | Gemini Pro + Opus | - |
| Simple refactoring | Sonnet | Gemini Flash |
