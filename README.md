# Openclaw
SKILL For OpenClaw

## Self-Improving Agent — Summary

A **single-file, browser-based AI tool** that helps you capture, analyze, and learn from mistakes and insights during AI agent sessions. Powered by Claude (Anthropic API).

---

### What It Does

**Dashboard — Learning Capture**
You paste in what happened — an error, a fix, a skill discovered, a note. Claude instantly analyzes it: categorizes the severity, names the underlying pattern, and gives a recommendation. Builds up a searchable archive over time.

**🐟 Mirofish — Knowledge Graph**
Turns your list of learnings into a live, animated mind map. Claude finds which learnings are semantically connected, then a physics simulation arranges them into clusters. You see *how* your knowledge is structured, not just what's in it.

**⚡ Skill Patterns — Pattern Library**
Claude extracts reusable strategy templates from your learnings in the form:
`When [situation] → Do [action] → Verify [outcome]`
You can also write your own. Hit "Apply" on any pattern to pre-fill the capture form with it.

**🤖 Claw Multi-Agent — Parallel Analysis**
Four Claude agents run simultaneously, each with a different job — finding root causes, extracting skills, building templates, finding the single highest-leverage fix. A fifth Coordinator agent reads all four outputs and produces a prioritized improvement plan.

---

### Key Facts

- **Zero dependencies** — one HTML file, open it in any browser
- **Your API key, your data** — key stored in sessionStorage only, never transmitted
- **Created by Joon Nyip (Koh)** — MIT License, open source on GitHub
