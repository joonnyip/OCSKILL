# Changelog

All notable changes to Self-Improving Agent are documented here.

Format: [MAJOR.MINOR.PATCH] — Date — Description

---

## [4.0.0] — 2026-04-16 — Full Roadmap Release

**Built by Claude (Anthropic) · Authored by Joon Nyip (Koh)**

### New Features
- **💾 LocalStorage Persistence** — Learnings, patterns, and custom agent prompts persist across browser sessions. Demo data only seeds on first run.
- **⬇ Export JSON** — Download all learnings + patterns as a structured JSON file.
- **⬇ Export Markdown** — Download a formatted Markdown report grouped by learning type, with analysis and recommendations included.
- **⬆ Import Transcript** — Upload any Claude transcript (.txt / .md / .json). Claude extracts key learnings automatically.
- **✏️ Custom Agent Prompts** — Edit each of the 4 Claw agent system prompts directly in the UI. Changes persist. Reset to defaults at any time.
- **🔍 Mirofish Zoom & Pan** — Mouse wheel to zoom, drag to pan. +/−/⊙ overlay controls. Zoom state preserved across rebuilds.
- **☀/🌙 Dark/Light Theme Toggle** — Full light theme with adapted colors. Toggle persists via localStorage.
- **📦 Shareable Learning Packs** — Export your learnings + patterns as a `.json` pack file. Others can import it to bootstrap from your knowledge base.

### Bug Fixes
- **BUG-SESSION** Fixed: API key was stored in `sessionStorage` — lost on every browser close. Migrated to `localStorage`.
- **BUG-MIRO-CLEAR** Fixed: Mirofish clear/rebuild was clobbering zoom control DOM nodes via `innerHTML`. Now uses targeted DOM removal.
- **BUG-DEMO-OVERWRITE** Fixed: Demo learnings were injected on every init(), overwriting any stored data. Now only seeds on first run (empty storage).

---

## [3.0.0] — 2025 — Initial Open Source Release

**Created by Joon Nyip (Koh)**

### New Features
- **🐟 Mirofish Enable** — Force-directed SVG knowledge graph. Claude finds semantic connections between learnings; nodes self-organize via physics simulation.
- **⚡ Skill Patterns** — Claude extracts reusable `When [X] → Do [Y] → Verify [Z]` templates from your learnings. Manual pattern creation also supported.
- **🤖 Claw Multi-Agent Improvement** — Four specialized agents (Error Detector, Skill Extractor, Pattern Builder, Optimizer) run in parallel via `Promise.all`. Coordinator agent synthesizes outputs into a prioritized plan.

### Core (inspired by pskoett/self-improving-agent)
- Learning capture with type classification: skill, error, correction, note
- Claude analysis per capture: severity, pattern, recommendation, tags
- Auto-extraction of patterns every 3 captures
- Activity feed with 12-item history
- Sidebar stats: learnings, patterns, errors

### Security & Quality Fixes
- **BUG-01** Fixed: Added `anthropic-version` header to all API calls
- **BUG-02** Fixed: API key modal with sessionStorage — enables standalone browser use
- **BUG-03** Fixed: XSS protection via `escapeHtml()` on all user-generated content
- **BUG-05** Fixed: `setInterval` stored and cleared on `beforeunload`
- **BUG-08** Fixed: Multi-agent coordinator card resets to hidden on re-run
- **BUG-09** Fixed: Pattern IDs use `String()` comparison — no float precision issues
- **BUG-11** Fixed: API response collects all text blocks, not just `content[0]`
- **STYLE-01** Fixed: `capturelearning` renamed to `captureLearning` (camelCase)
- Added `anthropic-dangerous-direct-browser-access: true` header for direct browser API access

### Developer Experience
- Single HTML file, zero build step, zero npm dependencies
- `'use strict'` mode throughout
- Structured state object `S` with clear ownership
- Cleanup on `beforeunload` (clearInterval, cancelAnimationFrame)
- Fixed Mirofish canvas uses internal 800×460 coordinate system — stable regardless of tab visibility

---

## Inspired By

- [self-improving-agent v3.0.13](https://clawhub.ai/pskoett/self-improving-agent) by [@pskoett](https://github.com/pskoett) — MIT-0 License
