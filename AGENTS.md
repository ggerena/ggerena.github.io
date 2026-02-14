# AGENTS.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static personal portfolio site for Gery Gerena (ggerena.cl), hosted on GitHub Pages. Redesigned as a terminal-style Markdown page — no frameworks, no build step, no package manager.

For the full redesign rationale and decisions, see [PLAN.md](./PLAN.md).

## Development

**No build commands.** Edit HTML/CSS/JS directly and push to `master` to deploy via GitHub Pages.

To preview locally, open `index.html` in a browser or use any static file server (e.g., `python -m http.server`).

## Architecture

- **index.html** — Single-page landing styled as Markdown rendered in a terminal. Monospace font, dark background, no images, no external dependencies. All CSS is inline.
- **index.md** — Pure Markdown version of the site content for AI/crawler consumption. Linked from the HTML via `<link rel="alternate" type="text/markdown">`.
- **404.html** — Custom error page.
- **CNAME** — Custom domain `ggerena.cl`.
- **assets/** — Legacy assets from the previous Golink Jekyll theme (not referenced by the current site).

## Key Details

- Asset URLs in HTML use root-relative paths (`/assets/...`), so local preview works with any static file server.
- No external CDN dependencies. Zero JavaScript.
