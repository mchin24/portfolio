# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Midnight Dev Studio** — personal portfolio site for Mychal Chin (Solutions Architect / Technical Lead). The site is fully static: plain HTML5, hand-rolled CSS3, and vanilla JavaScript. No build step, no framework, no dependencies.

- **Live domain:** midnightdev.studio (DNS via Cloudflare, hosted on DigitalOcean via Coolify)
- **Deployment:** manual push; no CI/CD currently

## Running the Site

Open `index.html` directly in a browser, or serve it with any static file server:

```bash
python3 -m http.server 8080
# or
npx serve .
```

There is no build step, package.json, or test suite.

## Architecture

Single-page layout (`index.html`) with one stylesheet (`css/styles.css`) and one script (`js/main.js`).

**`css/styles.css`** — all styles in one file, structured in labeled sections:
- CSS custom properties at `:root` (colors, spacing, font, transitions)
- Global reset, layout (`.container`, `.section`)
- Component blocks in order: Nav → Buttons → Hero → Projects → Coming Soon → Skills → About → Contact → Footer
- Responsive breakpoints: `1024px` (tablet), `900px` (narrow), `640px` (mobile), `420px` (small mobile)
- Scroll-in animation at the bottom (opt-in via `prefers-reduced-motion`)

**`js/main.js`** — three behaviors:
1. Sticky nav background (`scrolled` class added after 24px scroll)
2. Hamburger menu toggle (adds `open` to `.nav-links` and `.nav-hamburger`)
3. IntersectionObserver scroll-in animation (adds `visible` to `.project-card`, `.pipeline-item`, `.skill-group`, `.meet-card`)

**`design/`** — design reference files (PNG mockups + spec). `midnightdev-homepage-spec.md` is the authoritative spec for content, tone, and section structure. Consult it before adding or changing sections.

## Design Tokens

All visual constants live in `:root` in `styles.css`. Key values:

| Token | Value | Use |
|---|---|---|
| `--bg` | `#080c18` | Page background |
| `--surface` | `#0f1524` | Cards, sections |
| `--accent` | `#e8613a` | Highlight / emphasis |
| `--primary` | `#3563e9` | CTAs, links |
| `--text-muted` | `#7a8aaf` | Body copy |
| `--width` | `1140px` | Max container width |

## Brand & Tone

Tone is clean, professional, quietly confident — not corporate. First-person copy. No buzzwords. The "midnight" theme is reflected in deep navy colors and subtle details, not dramatic dark-mode aesthetics.

Audiences: hiring managers (want technical depth) and clients (want to see working projects). Content serves both.

## Content Structure

Sections in page order: Hero → Projects (Live) → Coming Soon (pipeline) → Skills → About → Contact → Footer.

Each **project card** includes: name, tagline, description, tech tags, live link, "What's Next" roadmap bullets, and card footer links.

Each **pipeline item** includes: name, one-line description, and a status badge (`Live` / `In Development` / `Planned`).

The `assets/emblem.svg` and the inline SVG clock logo in the nav/footer/hero are all the same Midnight Dev Studio emblem — keep them consistent if the logo changes.
