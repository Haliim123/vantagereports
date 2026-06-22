# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static single-page marketing website for **Vantage Reports** — a monthly business intelligence reporting service targeting UK SMBs. It consists of a single file: `index.html` (944 lines of self-contained HTML, CSS, and JavaScript). There is no build step, no package manager, and no backend.

The site is deployed via **GitHub Pages** with a custom domain (`vantagereports.uk`) configured in the `CNAME` file.

## Running Locally

Open `index.html` directly in a browser. No server or build process is needed.

## Architecture

Everything lives in `index.html`:

- **Styles** — embedded `<style>` block using CSS custom properties (`--navy`, `--gold`, `--cream`, `--grey`) defined on `:root`. Layout uses CSS Grid and Flexbox. Responsive breakpoint at `768px`.
- **JavaScript** — two functions at the bottom of the file:
  - `IntersectionObserver` that toggles `.visible` on elements with class `.reveal` as they scroll into view.
  - `handleSubmit(event)` called by the contact form — it suppresses default submission, hides the form, and shows a `#successMessage` div. **There is no real form backend.**
- **Sections** (in order): Hero → Problem → How It Works → Pricing → Who It's For → Contact → Footer

## Design System

| Token | Value |
|-------|-------|
| `--navy` | `#0D1B2A` |
| `--gold` | `#C9A84C` |
| `--cream` | `#F5F2EC` |
| `--grey` | `#8A96A3` |

**Fonts** (loaded from Google Fonts): Cormorant Garamond (headings/display), DM Sans (body).

Visual motifs: noise texture overlay (SVG `feTurbulence` filter), radial gradient glows on section backgrounds, subtle box shadows.

## Key Conventions

- All styles are co-located in the single `<style>` block — do not introduce external stylesheets unless restructuring the whole project.
- Animations are CSS-driven (`.reveal` → `.reveal.visible`); JavaScript only toggles the class.
- Pricing is hardcoded: Essentials £500/mo, Insights £1,200/mo, Intelligence £2,500/mo.
- The contact form does not submit anywhere — any real form integration would need a third-party service (e.g. Formspree, Netlify Forms) or a backend endpoint added to `handleSubmit`.
