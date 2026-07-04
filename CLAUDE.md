# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

`flowstateconsulting.com` — a static marketing + legal site for **Flow State
Technologies**, home to app privacy policies, terms, screenshots, and usage tips
for two apps: **MyCaddyMan** (iOS golf app) and **SafelySolo** (iOS/Android
personal-safety app). Plain HTML + one shared CSS file. No build step, no
dependencies, no JS framework. Served by GitHub Pages from `main` at the repo root.

## Working in it

- **No build, no bundler, no package manager.** Edit HTML/CSS directly; changes are the deploy.
- **Local preview:** `python3 -m http.server 8000` then open `http://localhost:8000`.
- **Deploy:** push to `main`. GitHub Pages serves `/ (root)`. `.nojekyll` makes Pages serve files as-is (no Jekyll processing). `CNAME` binds the custom domain.
- There are no tests, linters, or CI.

## Architecture

- **One stylesheet, `styles.css`, drives every page** — the landing page and all
  legal/policy pages. It's a small design system built on CSS custom properties
  (`:root`): a "Santa Cruz Pacific" color palette (`--tide`, `--surf`, `--sand`,
  etc.), a `clamp()`-based fluid type scale (`--step--1`…`--step-4`), and spacing
  tokens. Change design tokens here, not in individual pages. The recurring
  "current" motif (a thin animated wave line) is the signature element.
- **Each legal page lives in its own folder so its published URL is clean and
  stable** — these URLs get pasted into App Store / Play Store listings, so the
  paths are load-bearing and must not change:
  - `mycaddyman/privacy/index.html` → `/mycaddyman/privacy/`
  - `safelysolo/privacy/index.html` → `/safelysolo/privacy/`
  - `terms/index.html` → `/terms/`
- **All internal links are relative**, so the site works identically at the
  `github.io` project URL and at the custom domain. Keep them relative.
- Fonts (Hanken Grotesk + Newsreader) load from Google Fonts via `<link>`; no font files in the repo.
- `assets/` holds screenshots and store badges (see `assets/README.md`). The
  landing page currently uses placeholder blocks (`ph-note`) and placeholder
  store buttons instead of real images.

## Content status — read before editing pages

The privacy and terms pages are **starting drafts, not legal advice**, and the
landing page has placeholder content. Both carry inline `<!-- EDIT: -->` /
`REVIEW BEFORE PUBLISHING` comments marking what's unfinished:

- `[BRACKETED]` placeholders (dates, contact email, store URLs, SMS provider) must be filled in.
- Store links point at `#REPLACE_APP_STORE_URL` / `#REPLACE_PLAY_STORE_URL`; store buttons are plain placeholders, not the official Apple/Google badges.
- Data-practice statements must match what each app actually does, and stay consistent with the App Store "App Privacy" label and Google Play "Data safety" form. SafelySolo (contacts, precise location, SMS) is the sensitive one — accuracy matters most there.

See `README.md` for the full pre-publish checklist and custom-domain / DNS / email migration steps.
