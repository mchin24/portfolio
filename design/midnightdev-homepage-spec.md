# Midnight Dev Studio — Homepage Specification

**Version:** 0.1
**Domain:** [midnightdev.studio](https://midnightdev.studio) (Cloudflare)
**Updated:** May 2026

---

## 1. Overview

The Midnight Dev Studio homepage is a professional portfolio showcase for Mychal Chin — Solutions Architect and Technical Lead. The site serves two audiences: hiring managers evaluating technical credibility, and potential clients assessing fit for project work.

The site is static — no backend, no user accounts. It links out to live portfolio apps and public GitHub repositories.

---

## 2. Brand & Tone

**Name:** Midnight Dev Studio

**Tone:** Clean, professional, quietly confident. "Midnight" represents calm focus and productive stillness — the hours when good work gets done. Not moody or dramatic. Not generic corporate either.

**Visual direction:**
- Clean layout with generous whitespace
- Subtle nods to the midnight theme — deep navy or near-black accents, not full dark mode
- Typography-forward — let the content breathe
- Fun without being unprofessional — personality shows through writing and details, not gimmicks

---

## 3. Target Audience

**Primary:**
- **Hiring managers** — evaluating technical skills, project depth, and professional credibility
- **Potential clients** — assessing what has been built, that it works, and whether this is someone they can trust with a project

Both audiences are served by the same content — polished live projects speak to clients, technical depth and architecture decisions speak to hiring managers.

---

## 4. Positioning

**Mychal Chin — Solutions Architect / Technical Lead**

Someone who designs systems, leads delivery, and builds things that work. 25+ years of professional experience including enterprise software, customer implementations, and technical leadership. Currently building a modern full-stack portfolio spanning Node.js, React, Python, PostgreSQL, and AI integrations.

---

## 5. Tech Stack

| Layer | Technology |
|---|---|
| Markup | HTML5 |
| Styles | CSS3 (no framework — hand-rolled) |
| Interactivity | Vanilla JavaScript |
| Hosting | DigitalOcean via Coolify |
| DNS / Edge | Cloudflare |

No React. No build step required. Fast, simple, deployable anywhere.

**Future consideration:** Astro — static site framework, zero JS by default, growing industry traction. Worth evaluating for v2.

---

## 6. Site Sections

### 6.1 Hero

The first thing a visitor sees. Should load instantly and communicate clearly within 5 seconds.

**Content:**
- Name and title — Mychal Chin, Solutions Architect / Technical Lead
- One-line positioning statement — what you do and who you do it for
- Two CTAs — "View Projects" (scrolls down) and "Get in Touch" (scrolls to contact)

**Tone:** Confident and direct. No buzzword soup.

---

### 6.2 Live Projects

Showcase of deployed, working applications. Each project gets a card containing:

- Project name and tagline
- Brief description (2-3 sentences max)
- Tech stack tags
- Link to live app
- Link to public GitHub repo (where applicable)
- **"What's Next" teaser** — 2-3 bullet points of near-term planned updates, framed as a short roadmap

**Live Projects:**

| Project | URL | Repo |
|---|---|---|
| Nomacle | nomacle.midnightdev.studio | Private |
| Hangman Word Game | wordgame.midnightdev.studio | TBD |

---

### 6.3 Coming Soon

Pipeline projects that are in active development or planned. Signals momentum and breadth to both hiring managers and clients.

Each entry includes:
- Project name
- One-line description
- Status indicator (In Development / Planned)

**Pipeline projects to feature:**
- Auth Service — shared JWT authentication service
- Sports Analytics — NBA/NFL data pipelines and dashboards
- Restaurant QA Suite — Python test suite for API and end-to-end testing
- API Integration Hub — multi-API aggregation service
- Log Analysis CLI — Python server log analysis tool

---

### 6.4 Skills & Stack

A honest, scannable representation of technical skills. Not an exhaustive list — focused on what's relevant to the target audience.

**Categories:**
- Languages — JavaScript/TypeScript, Python, PHP, SQL
- Frontend — React, HTML5, CSS3, Tailwind CSS, shadcn/ui
- Backend — Node.js, Express
- Databases — PostgreSQL (pgvector), MySQL, SQLite
- Infrastructure — Docker, AWS (ECS, ECR, RDS, Secrets Manager), Terraform, GitHub Actions
- AI/APIs — OpenAI API, Claude API, Google Places API
- Testing — Jest, Supertest, Cucumber, Playwright, pytest
- Tools — Git, Cloudflare, Coolify, Grafana

**Note:** Distinguish actively used skills from skills in progress where appropriate.

---

### 6.5 About

A brief, human section. Not a resume — a person.

**Content:**
- Short bio — 25+ years building enterprise software, professional services leadership, now building a modern full-stack portfolio under Midnight Dev Studio
- What drives the work — solving real problems, clean architecture, shipping things that actually work
- Current focus — modern full-stack development, AI integrations, portfolio projects

**Tone:** First person, direct, no corporate speak.

---

### 6.6 Contact

Simple and low-friction.

**Content:**
- Brief invitation — open to full-time roles, contract work, and interesting projects
- Email link
- LinkedIn link
- GitHub link

No contact form for now — mailto link is sufficient for a static site.

---

## 6.7 Color Palette

Deep navy base with a single warm accent — subtle nods to "midnight," not full dark mode. Values match the CSS custom properties in `css/styles.css`.

| Swatch | Token | Hex / Value | Use |
|---|---|---|---|
| ![#080c18](https://placehold.co/40x20/080c18/080c18.png) | `--bg` | `#080c18` | Page background |
| ![#0f1524](https://placehold.co/40x20/0f1524/0f1524.png) | `--surface` | `#0f1524` | Cards, sections |
| ![#141d30](https://placehold.co/40x20/141d30/141d30.png) | `--surface-2` | `#141d30` | Nested/raised surfaces |
| ![#1c2640](https://placehold.co/40x20/1c2640/1c2640.png) | `--surface-3` | `#1c2640` | Hover states, tertiary surfaces |
| ![#eef2ff](https://placehold.co/40x20/eef2ff/eef2ff.png) | `--text` | `#eef2ff` | Primary text |
| ![#7a8aaf](https://placehold.co/40x20/7a8aaf/7a8aaf.png) | `--text-muted` | `#7a8aaf` | Body copy, secondary text |
| ![#3d4e72](https://placehold.co/40x20/3d4e72/3d4e72.png) | `--text-dim` | `#3d4e72` | Least prominent text (labels, meta) |
| ![#e8613a](https://placehold.co/40x20/e8613a/e8613a.png) | `--accent` | `#e8613a` | Highlight / emphasis (warm orange) |
| ![#3563e9](https://placehold.co/40x20/3563e9/3563e9.png) | `--primary` | `#3563e9` | CTAs, links (blue) |
| ![#2550cc](https://placehold.co/40x20/2550cc/2550cc.png) | `--primary-h` | `#2550cc` | Primary hover state |
| ![#22c55e](https://placehold.co/40x20/22c55e/22c55e.png) | `--green` | `#22c55e` | Status indicators (e.g. "Live") |
| — | `--border` | `rgba(255, 255, 255, 0.07)` | Default borders (translucent white) |
| — | `--border-h` | `rgba(255, 255, 255, 0.14)` | Hover borders (translucent white) |

**Usage notes:**
- Navy surfaces (`--bg` → `--surface-3`) establish depth without full dark-mode contrast.
- `--accent` (orange) and `--primary` (blue) are the only saturated colors — reserved for CTAs, links, and emphasis so they stay meaningful.
- `--green` is used sparingly, for status badges only (e.g. "Live" in Coming Soon).

## 6.8 Typography

Single typeface, differentiated by weight rather than a heading/body pairing — keeps the type system simple and consistent with the "no framework, hand-rolled" approach.

| Token | Value |
|---|---|
| `--font` | `'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif` |

Weights in use range from 500 (medium, body/labels) to 800 (extra-bold, hero/emphasis headings).

---

## 7. Navigation

Sticky top navigation with smooth scroll to each section:

```
Midnight Dev Studio    Projects    Coming Soon    Skills    About    Contact
```

Mobile-friendly — collapses to a hamburger menu on small screens.

---

## 8. Performance & SEO

- No external dependencies where possible — no jQuery, no heavy libraries
- Optimized images — WebP format, lazy loading
- Meta tags — title, description, Open Graph for link previews
- Semantic HTML — proper heading hierarchy, landmark elements
- Fast load target — under 1 second on a decent connection

---

## 9. Hosting & Deployment

- Deployed via Coolify on DigitalOcean
- DNS managed via Cloudflare
- No CI/CD required initially — manual deploy is fine for a static site
- Future: GitHub Actions for auto-deploy on push to main

---

## 10. Open Questions

- Final one-line positioning statement — to be written
- About section copy — to be written
- Hangman repo — public or private?
- Domain email — contact@midnightdev.studio or personal email?
