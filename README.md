# Self-Improving Agent

> An AI-powered self-improvement tool — capture learnings, visualize knowledge, extract skill patterns, and run multi-agent analysis. All in a single HTML file.

**Created by [Joon Nyip (Koh)](https://github.com/joonnyip)**  
MIT License · Powered by Claude (Anthropic)

---

## Features

### Core — Learning Capture
Capture learnings, errors, corrections, and notes from your AI agent sessions. Claude analyzes each entry and extracts:
- Severity level (low / medium / high)
- Underlying pattern name
- Actionable recommendation
- Tags for filtering

Auto-extracts skill patterns every 3 captures.

---

### 🐟 Mirofish — Knowledge Graph
Enable Mirofish to visualize your learnings as a live, force-directed knowledge graph.

- Claude finds semantic connections between learning nodes
- Nodes repel each other and edges attract — the graph self-organizes into natural clusters
- Color-coded by learning type (skill, error, correction, note)
- Rebuild the graph at any time to incorporate new learnings

---

### ⚡ Skill Patterns — Pattern Library
Claude extracts reusable strategy templates from your learnings:

```
When [SITUATION] → Do [ACTION] → Verify [OUTCOME]
```

- Auto-extracted every 3 learnings
- Manually add your own custom patterns
- Apply a pattern to pre-fill the capture form
- Track usage count per pattern

---

### 🤖 Claw Multi-Agent Improvement
Four specialized Claude agents run **in parallel**, each analyzing your learnings from a different angle:

| Agent | Focus |
|---|---|
| 🔍 Error Detector | Root causes & failure pattern analysis |
| ⚡ Skill Extractor | Teachable skill identification |
| 🧱 Pattern Builder | Generalizable improvement templates |
| 🚀 Optimizer | Highest-leverage improvement actions |

A fifth **Coordinator** agent synthesizes all four outputs into a prioritized improvement plan.

---

## Quick Start

### Option 1 — Open directly in browser

1. Download `index.html`
2. Open it in any modern browser (Chrome, Firefox, Safari, Edge)
3. Enter your [Anthropic API key](https://console.anthropic.com) when prompted
4. Start capturing learnings

### Option 2 — Clone and serve locally

```bash
git clone https://github.com/joonnyip/OCSKILL.git
cd OCSKILL

# Any static server works — e.g. Python:
python3 -m http.server 8080

# Then open http://localhost:8080
```

### Option 3 — Deploy to GitHub Pages

1. Fork this repository
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)`
4. Your app is live at `https://<username>.github.io/OCSKILL/`

---

## API Key

This app calls the Claude API directly from your browser.

- Your key is stored in `sessionStorage` — it is never logged, transmitted, or stored permanently
- You need an [Anthropic API key](https://console.anthropic.com) — standard pay-as-you-go pricing applies
- Each capture costs roughly $0.001–0.003 in API credits depending on length
- Click the ⚙ settings button at any time to update your key

---

## Project Structure

```
OCSKILL
├── index.html          # The entire app (single file, zero dependencies)
├── README.md           # This file
├── LICENSE             # MIT License
├── CONTRIBUTING.md     # How to contribute
└── CHANGELOG.md        # Version history
```

The entire application is a single HTML file with no build step, no npm, no external dependencies beyond Google Fonts (for typography) and the Anthropic API (for AI features).

---

## Browser Requirements

| Browser | Minimum Version |
|---|---|
| Chrome / Edge | 90+ |
| Firefox | 88+ |
| Safari | 14+ |

Requires an internet connection for:
- Google Fonts (UI typography)
- Anthropic API (AI features)

---

## Roadmap

- [ ] LocalStorage persistence across sessions
- [ ] Export learnings as JSON / Markdown
- [ ] Import learnings from Claude transcript files
- [ ] Custom agent prompts
- [ ] Mirofish zoom & pan
- [ ] Dark/light theme toggle
- [ ] Shareable learning packs

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## Credits

Inspired by [self-improving-agent](https://clawhub.ai/pskoett/self-improving-agent) by [@pskoett](https://github.com/pskoett) on ClawHub.

Built on top of [Claude](https://claude.ai) by [Anthropic](https://anthropic.com).

---

## License

MIT License — see [LICENSE](LICENSE) for full text.

Free to use, modify, and redistribute. Attribution appreciated but not required.

---

*Created by Joon Nyip (Koh)*
