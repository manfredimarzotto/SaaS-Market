# SaaS-Market

Live: https://manfredimarzotto.github.io/SaaS-Market/

## What This Is

A multi-page static site visualizing AI and SaaS market dynamics — budget shifts, category divergence, and adoption curves. Each page is a standalone HTML file with its own styles and interactivity.

## Repo Structure

```
SaaS-Market/
├── index.html                          # Page 1: AI Budget Scaling overview (bar chart + key themes)
├── ai-divergence.html                  # Page 2: AI Divergence by Category & Segment (WIP)
├── ai-saas-considerations-booklet.md   # Source content / build spec reference
└── README.md
```

## Pages

| File | Status | Description |
|------|--------|-------------|
| `index.html` | Complete | Horizontal bar chart showing likely spend increases/decreases across AI enablers and traditional software categories, with key themes sidebar |
| `ai-divergence.html` | In progress | AI/SaaS category divergence and adoption curves — hero section built, two-column layout (Category Divergence + Adoption Curves by Vertical) pending |

## Tech Stack

- **Page 1** (`index.html`): Vanilla HTML/CSS/JS, Inter font, IntersectionObserver animations
- **Page 2** (`ai-divergence.html`): React 18 via CDN + Babel, inline styles, Instrument Serif / DM Sans / DM Mono fonts, custom `useInView` hook for scroll animations

## Branches

| Branch | Purpose |
|--------|---------|
| `main` | Stable — contains the completed Page 1 |
| `claude/add-ai-dive-page-two-PUSM8` | Active development — building Page 2 (ai-divergence.html) |

Pages are kept as separate files during development and can be linked or merged once finalized.
