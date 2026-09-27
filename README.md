# Lade Coder — Working Prototype

> A polished **single-file AI website builder** (Lovable/Bolt-style) in pure HTML/CSS/JS. Describe the website you want in plain language, pick a model, and get a live, previewable page in seconds — then iterate with a persistent chat, restore earlier versions, and download the final HTML.

This is the evolved **working prototype** of Lade Coder — a bigger, more refined successor to `Lade-Coder-basic-working-Prototype`, with typing indicators, robust code-block extraction, version history, and a cleaner chat UX. No build step, no dependencies — the entire app is one `index.html`.

Live demo: https://girishlade111.github.io/Lade-Coder-Working-Prototype/

## Features

- **Prompt → website** — describe your site ("landing page for a coffee shop") and the app generates a complete HTML page
- **3 model options**:
  - 🚀 **Qwen Coder** (fast) — `qwen/qwen3-coder:free` via OpenRouter
  - 🌟 **Kimi Dev** (powerful) — `moonshotai/kimi-dev-72b:free` via OpenRouter
  - Hugging Face fallback — `microsoft/Phi-3-mini-4k-instruct` via HF Inference API
- **Live preview + code tabs** — rendered site in a sandboxed `<iframe>` or raw source in a monospace code block
- **Follow-up chat** — keep refining with natural language ("add a pricing section"); the current code is sent as context and the full page is regenerated
- **Version history** — every generation is saved; one-click restore rolls back to the previous version
- **Download as HTML** — export the finished page as `lade-coder-project.html`
- **Code extraction** — smart parser pulls the ```` ```html ```` block out of model responses; errors surface in the preview instead of breaking the app
- Typing indicator while generating, animated chat messages, gradient/funky UI theme

## How It Works

1. Enter your OpenRouter / Hugging Face API keys where configured in the file (see "API keys")
2. Open `index.html`, pick a model, describe your site, hit send
3. The model is prompted to return *only* a complete ```` ```html ```` page
4. The app extracts the code, renders it in a sandboxed `<iframe>`, and stores it in history
5. Use the chat to iterate, restore earlier versions with **Restore**, and **Download** the final HTML

## Quick Start

No build tools required:

```bash
# Option 1: just open it
open index.html          # or double-click the file

# Option 2: serve it (avoids some file:// quirks)
npx serve .
# → http://localhost:3000
```

## Project Structure

```
index.html    # the whole app: chat UI, preview/code tabs, code extractor,
              # OpenRouter + Hugging Face clients, version history,
              # restore & download logic
```

## API Keys

The prototype calls the OpenRouter and Hugging Face APIs directly from the browser. Both keys live at the top of the `<script>` block (`OPENROUTER_API_KEY`, `HUGGINGFACE_API_KEY`) and the committed values are redacted — paste your own:

- **OpenRouter** — free key at https://openrouter.ai/keys (use the `:free` models)
- **Hugging Face** — token at https://huggingface.co/settings/tokens

## Security Note

This is a *prototype* — API keys entered client-side are visible in page source. For a production version, proxy API calls through your own backend and never ship secret keys in client-side code.

## Deployment

Fully static — deploy by hosting `index.html`:

- **GitHub Pages** — live at https://girishlade111.github.io/Lade-Coder-Working-Prototype/ (the `gh-pages` branch contains exactly this repo's root)
- **Any static host** (Cloudflare Pages, Netlify, Vercel) — upload the single file

---

Built by Girish Lade — https://ladestack.in
