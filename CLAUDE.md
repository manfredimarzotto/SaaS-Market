# CLAUDE.md — Project Guidelines

## Project Overview
Single-page AI SaaS market overview site. All markup, styles, and scripts live in `index.html`.

## Branch & Merge Conflict Prevention

### Root Cause (March 2026 incident)
Two feature branches diverged from the same commit (`73f666e`) and both rewrote `index.html`:
- `claude/convert-to-markdown-spec-02HGt` — fully replaced the dark-mode booklet with a new light-themed single-page design (1370 lines deleted, 461 added)
- `claude/review-codebase-TELmm` — added UI enhancements (hover effects, cursor, dynamic bg) to the OLD design

Because both branches rewrote the same monolithic file independently, the merge produced a full-file conflict that could not be auto-resolved.

### Remediation Rules

1. **Always fetch and check the target branch before starting work.**
   ```
   git fetch origin
   git log --oneline --all --graph
   ```
   If the target branch has moved ahead, rebase or merge it into your working branch BEFORE making changes.

2. **Never work on a stale base.** If another branch is actively modifying `index.html`, coordinate — either wait for it to merge or branch off from it directly.

3. **Prefer small, incremental PRs over large rewrites.** A full-file rewrite on one branch while another branch edits the same file guarantees conflicts.

4. **When the project has a single monolithic file (`index.html`)**, treat it as a high-contention resource. Only one branch should make large structural changes at a time.

5. **If a conflict does occur**, favour `--theirs` for the structural base when one branch is a rewrite and the other is incremental enhancements, then re-apply enhancements on top. Never blindly accept `--ours` on a rewritten file.

6. **Before merging, rebase the branch onto the latest `main`** to resolve conflicts locally rather than in the PR.
   ```
   git fetch origin main
   git rebase origin/main
   git push --force-with-lease
   ```

## Content & Copy Rules
- **All text should render on a single line** where possible — use `white-space: nowrap` or remove `max-width` constraints as needed
- **No hard stops (periods) at the end of sentences** — omit trailing periods on headings, subtitles, bullet points, card text, footer banners, and body copy. Abbreviations like "Mgmt." are fine

## Design System (Current — Light theme)
- **Font:** Inter (300–800), with weight hierarchy: 800 headings, 600 emphasis, 400 body, 300 subtitles
- **Background:** Light `#EFF3F8` with animated gradient orbs + grid lines
- **Text colors:** Headings `#0F1629`, body `#3A3F4B`, secondary `#6B7280`, muted `#9CA3AF`
- **Accent palette:** Blue `#5B8DEF`, Teal `#0D6E6E` / `#2DD4BF`, Green `#34D399`, Red `#EF4444` / `#F87171`, Yellow `#FBBF24`, Purple `rgba(139,92,246)`
- **Cards:** Glassmorphism — `rgba(255,255,255,0.65)` bg, `rgba(0,0,0,0.06)` borders, `backdrop-filter: blur(12px)`
- **Layout:** CSS Grid (`1fr 360px`) for chart + themes side-by-side
- **Bar chart:** 24px height bars, 34px row height, 6px gap — more breathing room
- **Hover:** Bars glow with brightness; theme cards get subtle bg + border
- **Animations:** IntersectionObserver fade-in (0.7s cubic-bezier), staggered bar width transitions (60ms per bar)
- **Dynamic bg:** 3 blurred gradient orbs (blue, teal, purple) on `#EFF3F8`, animated grid lines, subtle noise texture
