# Repository Guidelines

This repo powers [baixiaosheng.de](https://www.baixiaosheng.de), the personal landing page and open-source project hub for Baixiaosheng. It is a static single-page site with no build step.

## Project Structure & Module Organization

The application lives entirely in `index.html` (≈707 lines): inlined sections (`#home`, `#about`, `#experience`, `#projects`, `#skills`, `#contact`), a `<style>` block with the custom theme (glass-card, terminal, fonts), and a `<script>` block holding the `i18n` table (`zh`, `en`) and DOM helpers. `README.MD` and `LICENSE` (MIT, 2026) round out the repo. There is no bundler, no `src/`, and no `tests/`; Tailwind, Font Awesome, and Google Fonts are loaded from CDN inside the page.

## Build, Test, and Development Commands

No buildtool is configured. Serve and preview locally with any static server:

```bash
python3 -m http.server 8000   # then open http://localhost:8000/index.html
```

Verify visually: check the hero, projects, skills, and contact sections at narrow (≈375px) and wide (≥1280px) viewports, toggle the `lang-zh` / `lang-en` buttons, and confirm external links point at the URLs in `README.MD`.

## Coding Style & Naming Conventions

HTML is authored Chinese-first (`lang="zh-CN"`) with English mirrored through the inline `i18n` object. Visible text must be updated under both `zh` and `en` keys on the matching `data-i18n` attribute. Style mixes Tailwind utilities with a small custom vocabulary (`glass-card`, `card-hover`, `terminal`, `skill-badge`, `nav-link`) and hex/alpha color tokens; keep new CSS in the single `<style>` block. Preserve the two-space indentation and single-file layout — don't split assets or introduce a bundler without updating this guide and `README.MD`.

## Testing Guidelines

No automated test suite exists yet. Treat the manual checks above as the baseline. If you add a lint, link-checker, or CI, document it here.

## Commit & Pull Request Guidelines

History uses short, lowercase, area-scoped imperative messages: `update blog`, `update lang-zh`, `first init`. Match that style (e.g. `adjust hero spacing`, `fix i18n typos`). PRs should be one concern at a summary plus affected `#id` ranges, a screenshot or recording for visual changes, and matching updates to `README.MD` when project or contact details change.

## Security & Configuration Tips

The only dynamic behavior is `copyEmail()`, which copies the public contact email on card click — not a secret. Keep outbound links using `rel="noopener noreferrer"`. Don't hard-code tokens or internal URLs; there's no server side to protect them. The copyright year sits in the footer — update it alongside substantive releases.
