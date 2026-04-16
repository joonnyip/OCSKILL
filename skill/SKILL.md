---
name: ocskill
description: >
  AI-powered self-improvement tool for OpenClaw agents. Captures learnings,
  errors, and corrections from agent sessions, analyzes them with Claude,
  visualizes knowledge connections (Mirofish graph), extracts reusable skill
  patterns, and runs 4 parallel Claude agents to produce a prioritized
  improvement plan. Use when an agent session produces errors, unexpected
  results, or lessons worth retaining across sessions.
version: 1.0.0
metadata:
  openclaw:
    requires:
      env:
        - ANTHROPIC_API_KEY
      bins:
        - curl
    primaryEnv: ANTHROPIC_API_KEY
    homepage: https://github.com/joonnyip/OCSKILL
    emoji: "⟳"
    tags:
      - self-improvement
      - learning
      - memory
      - patterns
      - multi-agent
      - knowledge-graph
---

# OCSKILL — Self-Improving Agent

Created by **Joon Nyip (Koh)** · MIT License · [GitHub](https://github.com/joonnyip/OCSKILL)

## When to use this skill

Use OCSKILL when:
- A command or tool call fails unexpectedly
- You catch yourself making the same mistake more than once
- A user corrects your approach or output
- You discover a faster, cleaner, or more reliable way to do something
- You finish a complex session and want to retain the key lessons
- You want to see patterns in your recent errors or improvements

## How to use this skill

### 1 — Capture a learning

When something notable happens (error, correction, insight), record it:

```
LEARNING TYPE: error | correction | skill | note

CONTENT:
<describe what happened, what failed, what was learned>
```

Claude will analyze the entry and extract:
- Severity (low / medium / high)
- Underlying pattern name
- Actionable recommendation
- Tags for future retrieval

Every 3 captures, Claude auto-extracts **Skill Patterns** — reusable templates:
```
When [SITUATION] → Do [ACTION] → Verify [OUTCOME]
```

### 2 — Run the Mirofish knowledge graph

After capturing 3+ learnings, enable Mirofish to visualize connections:
- Claude maps semantic relationships between your learnings
- Force-directed graph clusters related concepts automatically
- Color-coded by type: skill (purple), error (red), correction (orange), note (cyan)

### 3 — Run Multi-Agent improvement analysis

When you want a deep analysis of accumulated learnings, trigger the 4-agent run:

| Agent | Role |
|---|---|
| 🔍 Error Detector | Root causes & failure pattern analysis |
| ⚡ Skill Extractor | Teachable skill identification |
| 🧱 Pattern Builder | Generalizable improvement templates |
| 🚀 Optimizer | Highest-leverage action identification |

A **Coordinator** agent synthesizes all 4 outputs into a prioritized plan (1–5 ranked actions).

### 4 — Apply a skill pattern

When a relevant pattern exists, apply it:
```
Applying pattern: <Pattern Name>

When [situation] → Do [action] → Verify [outcome]
```

## Quick Start — Web UI

The full OCSKILL interface runs in any browser as a single HTML file:

```bash
# Clone and open
git clone https://github.com/joonnyip/OCSKILL.git
cd OCSKILL
open index.html   # macOS
xdg-open index.html  # Linux
```

Enter your Anthropic API key when prompted. The key is stored in `sessionStorage` only — never transmitted elsewhere.

## Quick Start — Agent-native (no UI)

To use OCSKILL directly inside an OpenClaw agent session, call the capture API:

```bash
curl -s https://api.anthropic.com/v1/messages \
  -H "x-api-key: $ANTHROPIC_API_KEY" \
  -H "anthropic-version: 2023-06-01" \
  -H "content-type: application/json" \
  -d '{
    "model": "claude-sonnet-4-20250514",
    "max_tokens": 400,
    "system": "You are a self-improvement analyzer. Given a learning entry, return ONLY valid JSON: {\"summary\":\"1 sentence\",\"category\":\"skill|error|correction|note\",\"severity\":\"low|medium|high\",\"pattern\":\"pattern name\",\"recommendation\":\"1-2 sentence action\",\"tags\":[\"tag1\",\"tag2\"]}",
    "messages": [{"role":"user","content":"Type: error\nContent: <WHAT HAPPENED HERE>"}]
  }' | python3 -c "import sys,json; d=json.load(sys.stdin); print(json.dumps(json.loads(d['content'][0]['text']), indent=2))"
```

## Storage

Learnings are stored in-session (browser `sessionStorage`). For persistence across sessions, export from the web UI as JSON and store in your workspace.

## Security

- API key stored in `sessionStorage` only — cleared on tab close
- All user-generated content is XSS-escaped before rendering
- No data sent to any third party beyond the Anthropic API
- `'use strict'` mode throughout
- `anthropic-dangerous-direct-browser-access: true` header set for direct browser API calls

## Bugs fixed in v1.0.0

All 8 known issues resolved: `anthropic-version` header, API key modal with sessionStorage, XSS escaping (29 call sites), camelCase function naming, `setInterval` cleanup, coord-card re-run reset, String ID comparison, multi-block API response collection.

## Roadmap

- [ ] LocalStorage persistence across sessions
- [ ] Export learnings as JSON / Markdown
- [ ] Import from Claude transcript files
- [ ] Custom agent prompts
- [ ] Mirofish zoom & pan
- [ ] Shareable learning packs

## Credits

Inspired by [self-improving-agent](https://clawhub.ai/pskoett/self-improving-agent) by [@pskoett](https://github.com/pskoett) on ClawHub · Built on [Claude](https://claude.ai) by Anthropic
