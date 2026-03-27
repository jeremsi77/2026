# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Static marketing website for **Althörnli**, a farm in the Tösstal (Canton Zürich). German language (lang="de"). No build tools, frameworks, or dependencies — pure HTML/CSS served via GitHub Pages.

**Live site:** https://jeremsi77.github.io/2026/

## Development

Open `index.html` in a browser. No build step, no dev server required. For live reload during development, use any static server (e.g. `python3 -m http.server`).

## Architecture

Single-page site with three files:

- `index.html` — page structure and content
- `css/style.css` — all styles
- `images/` — 13 web-optimized JPGs with descriptive names (hero-*, hof-*, verweilen-*, produkte-*, news-*)

## CSS Design System

Custom properties define the palette in `:root`:
- `--cream` / `--cream-dark` — backgrounds
- `--green` — accent / CTA (Kontakt band)
- `--brown` — eyebrow labels, dividers
- `--muted` — body text
- `--dark` — headings, nav
- `--white` — card/section-band backgrounds

Typography: Cormorant Garamond (headings), Inter (body). Both loaded from Google Fonts.

Two responsive breakpoints: **1000px** (grid collapse) and **720px** (mobile — nav links hidden, single-column).

## Deployment

Hosted on GitHub Pages. Repository: `jeremsi77/2026`.

A GitHub Actions workflow (`.github/workflows/deploy.yml`) handles deployment:
- **Automatic:** every push to `main` triggers a deploy
- **Manual:** can also be triggered via `workflow_dispatch` (`gh workflow run deploy.yml`)
- The workflow checks out the repo, uploads the entire root as an artifact, and deploys it to the `github-pages` environment

To deploy changes: commit and push to `main`. That's it — the action runs automatically. To check deploy status: `gh run list --workflow=deploy.yml`.

## Content Editing

Each page section is a clearly marked HTML block (`<!-- ─ SECTION NAME ─── -->`). Image `src` paths point to `images/`. The `Photos/` directory holds source originals and is gitignored.
