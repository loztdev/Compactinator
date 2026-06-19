# Compactinator 🗜️

An accuracy-first **context compaction front end for [OpenRouter](https://openrouter.ai)**.

Paste a long conversation, transcript, document, or context dump — Compactinator
rewrites it into the most compact form it can **without losing information**, then
independently audits the result, finds anything that was dropped, and re-compacts
to restore it. It loops until it hits your target fidelity (default **100% —
lossless**). Compression rate is deliberately sacrificed for accuracy.

## Features

- **Dark-mode-first**, single self-contained `index.html` — no build, no server, no dependencies.
- **Runs anywhere with a browser**, including Android. Use "Add to Home screen" for an app-like, installable experience.
- **Accuracy-first compaction loop**: compact → audit fidelity → restore missing facts → repeat to target.
- **Token tracker** — original vs. compacted content tokens, plus cumulative OpenRouter API usage (prompt + completion) across the session.
- **Compaction-rate tracker** — percentage / token reduction.
- **Accuracy estimator** — independent fidelity audit scored 0–100%, with an audit trail listing exactly what was restored on each pass.
- **Live model list** fetched from OpenRouter, with a free-type fallback.

## Usage

1. Open `index.html` in any modern browser (desktop or mobile).
2. Open **Settings**, paste your OpenRouter API key (stored only in your browser's
   `localStorage` — it never leaves your device), and pick a model.
3. Paste text, tap **Compact**, and read the trackers + audit trail.

Optionally set a target accuracy below 100% and a max number of refine passes if
you want to cap cost/latency.

## Privacy

Everything runs client-side. Your API key and text are sent **only** to the
OpenRouter API directly from your browser. Nothing is sent anywhere else.
