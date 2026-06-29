# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

CSVsplit is a single-file, fully client-side CSV splitting tool. The entire app lives in `index.html` — HTML structure, CSS, and JavaScript are all inline. There is no build step, no framework, no package manager, and no test suite.

## Running the App

Open `index.html` directly in a browser, or serve it with any static file server:

```sh
python3 -m http.server 8080
# then open http://localhost:8080
```

## Architecture

All logic is in the `<script>` block at the bottom of `index.html`. Key sections marked with comments:

- **State** — three module-level vars: `allRows`, `originalFilename`, `splitParts`
- **Upload zone** — drag-and-drop + file input click handler → `handleFile()`
- **Parse** — PapaParse (loaded from CDN) parses the CSV; header row is `allRows[0]`, data rows are `allRows.slice(1)`
- **Split** — `runSplit()` chunks data rows by `chunkSize`, prepending the header to each chunk
- **Render results** — `renderResults()` builds DOM nodes for each part with staggered animation delays
- **Download** — `downloadPart()` uses `Papa.unparse()` + `URL.createObjectURL` blob download
- **Error / Reset** — inline error display with auto-dismiss timer; reset restores upload zone

## Design System

CSS custom properties are defined in `:root`. The palette is dark-mode only:
- `--bg` / `--surface` / `--surface-2` — layer backgrounds
- `--accent` (`#b8ff00`) — lime green used for all interactive highlights
- `--text` / `--text-dim` / `--text-muted` — text hierarchy
- `--mono` / `--sans` / `--display` — three font stacks (JetBrains Mono, DM Sans, Syne)

All processing happens in the browser — no data is ever sent to a server.
