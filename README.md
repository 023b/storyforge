# StoryForge

A single-file, no-signup story writing tool with AI proofreading, worldbuilding notes, timeline, and character relationship tracking — all running in your browser.

**Live: https://023b.github.io/storyforge/**

## What it does

- **Chapters** — write and organize multi-chapter stories in a distraction-free editor
- **AI Check** — grammar/style proofreading powered by any model on OpenRouter, with inline highlights and one-click fixes
- **Notes & World** — freeform space for lore, locations, rules
- **Timeline** — plot events in order, linkable to characters
- **Characters** — character cards with a relationship graph (drag to connect)
- **Import** — bring in existing work as `.txt`, `.md`, or `.docx`, or restore a full project backup
- **Export** — `.txt`, `.md`, `.html`, Word (paste method), or full JSON backup
- **Dark/light theme**, persisted
- **Crash recovery** — autosaves every few seconds; a floating restore button (bottom-right) recovers your last draft even if the tab closes unexpectedly

## Why it's just one HTML file

No backend, no build step, no server. Open the file (or the GitHub Pages link) and it works. All your writing stays in your browser's local storage — nothing is uploaded anywhere except the text you explicitly send to OpenRouter for a check.

## Setup

1. Open the [live link](https://023b.github.io/storyforge/) (or download `index.html` and open it locally).
2. Get a free API key at [openrouter.ai/keys](https://openrouter.ai/keys) — no card required.
3. Paste it in on first launch. Your key is stored only in your browser (`localStorage`) — StoryForge has no server, so there's nothing to leak it to.
4. Pick a model. The dropdown fetches OpenRouter's live model list and surfaces a free pick, a second free pick, and two paid options (in case a free model chokes on tricky edge cases) — or type in any model ID yourself via "Custom model…".

## Running it locally

It's one HTML file. Download `index.html`, double-click it. Done.

If you want to self-host:
```bash
git clone https://github.com/023b/storyforge.git
cd storyforge
# open index.html, or serve it with any static server
python3 -m http.server 8000
```

## Privacy

Everything — chapters, notes, timeline, characters, your API key — lives in your browser's `localStorage`. Nothing touches a server StoryForge controls. The only outbound calls are:
- OpenRouter's `/models` endpoint (no key required, just fetches the current model list)
- OpenRouter's `/chat/completions` endpoint (your text + your key, direct to OpenRouter, when you run a Check)

## Known limitations

- `localStorage` is per-browser, per-device — no sync across devices (by design; there's no account system)
- Free OpenRouter models have rate limits (typically 20 req/min) and availability can shift day to day — that's an OpenRouter-side constraint, not this app's
- Word export uses a paste-into-Word method rather than generating a native `.docx` binary

## License

MIT — do whatever you want with it.

## Feedback

Open an issue, or fork it and make it yours.
