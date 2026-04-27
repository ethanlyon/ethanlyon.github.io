# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev       # Start dev server at localhost:4321 (hot reload enabled)
npm run build     # Build for production to ./dist/
npm run preview   # Preview production build locally
```

## Architecture

Astro 6 static site with Tailwind CSS v4 (via `@tailwindcss/vite`). No framework components — all pages are `.astro` files.

**Layout:** `src/layouts/Layout.astro` is the single shared layout. It renders the header nav (with active-state `> label` prefix), main slot, and footer. Active page is detected via `Astro.request.url`.

**Pages:** Each page uses a numeric section label (`001 / home`, `002 / work`, etc.). Page content data (projects, publications, experience, skills, posts) is defined as inline arrays at the top of each `.astro` file — no CMS or external data source.

**Styling:** Design tokens live in `src/styles/global.css` as CSS variables (`--bg`, `--text`, `--accent` #c8b560 gold, `--muted`, `--border`, `--surface`). The `.bracket-box` class draws NieR Automata-style corner brackets via `::before`/`::after`. Tailwind is available but the site primarily uses inline styles and the global CSS classes.

**Static assets:** `public/` serves files at the root path — contains `resume.pdf`, `EMBC_BHVAR_FINAL.pdf`, and favicons.

**Contact form:** Formspree action URL still has `YOUR_FORM_ID` placeholder — not yet functional.
