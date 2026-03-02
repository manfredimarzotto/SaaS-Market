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

## Design System (Current)
- **Font:** Inter (400–800)
- **Palette:** Navy `#0A3D62`, Teal `#0D6E6E`, Green `#4CAF50`, Red `#C0392B`
- **Background:** Light `#F8F9FA` with dynamic animated orbs
- **Layout:** CSS Grid (`1fr 340px`) for chart + themes side-by-side
- **Animations:** IntersectionObserver-based fade-in + bar width transitions
- **Cursor:** Custom SVG pin in navy/teal gradient
