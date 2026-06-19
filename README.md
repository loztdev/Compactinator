# Compactinator 🗜️

A dark-mode **markdown chat front end for [OpenRouter](https://openrouter.ai)** with
built-in, accuracy-first **conversation compaction**.

Chat with any OpenRouter model, then losslessly compact long conversations:
Compactinator rewrites the transcript into the most compact form it can **without
losing information**, independently audits the result, finds anything dropped, and
re-compacts to restore it — looping until it hits your target fidelity (default
**100% — lossless**). Compression rate is deliberately sacrificed for accuracy.

## Features

### Chat
- **Markdown rendering** for **both** your messages and the AI's (code blocks, lists, tables, quotes, links — all escaped/safe).
- **Streaming responses** with a stop button.
- **Edit** any message (yours or the AI's), **regenerate** AI responses, copy, or delete.
- **System prompts** per chat, plus a **saved-prompt library** (name, load, delete).
- **Live model list** from OpenRouter (per-chat model), with a free-type fallback.

### Saving & files
- **Auto-save** — every chat continuously saves itself to its existing record; re-saving updates in place instead of duplicating. No save button needed.
- **Save all chats** — one-tap export of every chat + prompt to a single backup file.
- **Smart import** — re-importing a backup **updates chats that already exist (matched by ID, newest wins)** rather than creating copies, and adds new ones.
- **Export this chat → Markdown**.

### Trackers
- **Token tracker** — live conversation token estimate + cumulative OpenRouter API usage (prompt + completion + call count).
- **Compaction-rate tracker** — % / token reduction of the last compaction.
- **Accuracy estimator** — independent fidelity audit scored 0–100%, with an audit trail listing exactly what was restored on each pass.

### Everywhere
- **Dark-mode-first**, single self-contained `index.html` — no build, no server, no dependencies.
- **Runs in any browser, including Android.** Use "Add to Home screen" for an installable, app-like experience.

## Usage

1. Open `index.html` in any modern browser (desktop or mobile).
2. Open **Settings** (⚙️), paste your OpenRouter API key (stored only in your
   browser's `localStorage` — it never leaves your device), and pick a model.
3. Optionally set a **system prompt** (🧠), then chat.
4. Tap **🗜️** to compact a long conversation; read the trackers + audit trail (📊).

Set a target accuracy below 100% or a max number of refine passes if you want to
cap cost/latency.

## A note on "auto-updating files"

Browsers on Android can't silently write to files on disk (the File System Access
API is desktop-only). Compactinator achieves the same intent in a way that works
everywhere: chats **auto-save** and update in place as you go, "Save all" produces a
single portable backup, and **import merges by ID** so existing chats are updated
rather than duplicated.

## Privacy

Everything runs client-side. Your API key and text are sent **only** to the
OpenRouter API directly from your browser. Nothing is sent anywhere else.
