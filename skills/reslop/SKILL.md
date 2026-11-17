---
name: reslop
description: Restyle an existing frontend so it looks AI-generated on purpose. Purple gradients, glassmorphism, Inter, bento grids, suspicious metrics. Three levels (classic, hard, max) plus a read-only slop score. Use when the user runs /reslop or explicitly asks to make their site look AI-generated or "reslopped". Not for normal design work.
argument-hint: "[classic|hard|max|score] [extra notes]"
# lets it read its own mode files without a permission prompt
allowed-tools: Read(/${CLAUDE_SKILL_DIR}/references/**)
---

# Reslop

Make the site look like Claude built it in one prompt. You know the look. Centered hero, gradient headline, three cards with icons in rounded squares, purple everywhere.

The joke only works if the app still works. We're ruining the design, not the code.

## Pick a mode

Input: `$ARGUMENTS`

| Input | Mode | Read, in order |
|---|---|---|
| nothing, or `classic` | classic | `classic.md` |
| `hard` | hard | `classic.md`, `hard.md` |
| `max` | max | `classic.md`, `hard.md`, `max.md` |
| `score` | score | `score.md` only. Don't edit anything. |

The files live in `${CLAUDE_SKILL_DIR}/references/`. Modes stack: hard is classic plus more, max is hard plus everything. When two files disagree, the later one wins.

Anything after the mode word is extra instructions (`/reslop max but leave the docs pages alone`). Follow them. If the user asked in plain words instead of a command, pick the closest mode. "Go all the way" means max.

Each mode has to look different in a screenshot. Classic is light, tidy and believable. Hard is dark, glassy and glowing. Max is every AI landing page merged into one with nobody around to stop it. If your hard result could pass for classic, you held back.

## 1. Look first

- **Git.** If there are uncommitted changes, stop and ask before going further. Reslop touches a lot of files and people will want a clean undo.
- **Stack.** Read `package.json` (or whatever the project has) and the config files. Framework, router, how styles are written (Tailwind v3 or v4, CSS modules, plain CSS, styled-components, a component library), where global styles and theme tokens live, how fonts load.
- **What it is.** Read the main pages. A bike shop stays a bike shop. It just becomes "the AI-native platform for your ride". Real names, prices, hours, product data and docs stay.
- **What's visible.** Layout shell, navbar, landing page, cards, buttons, footer. That's where the change shows. Settings pages and admin tables get the theme and not much else.
- **Current slop level.** If it already has gradients and a bento grid, start from there and push. Don't reset it to plain first.

## 2. Change things in this order

Highest visual impact first, so the screenshot changes even if you run out of steam.

1. **Theme.** Fonts, colors, background, radius, shadows. One edit to the global CSS or Tailwind theme does half the job.
2. **Navbar.**
3. **Hero.** Headline, eyebrow badge, buttons, background effects.
4. **Sections and cards.** Features, lists, pricing, testimonials, footer.
5. **Small stuff.** Buttons, badges, inputs, links, focus rings.
6. **Decoration and motion.**
7. **Copy.**

The mode files describe a full landing page. Use the parts that fit. If the project is an app rather than a marketing site (dashboard, tool, docs), restyle what's there and give its headers and empty states the marketing treatment. Don't bolt a pricing section onto a todo app. Max gets more leeway here.

## 3. House rules

Use what the project already uses.

- Tailwind: write Tailwind. Arbitrary values (`bg-[radial-gradient(...)]`) are fine. Keyframes and anything gnarly go in the global CSS file. v4 sets the theme with `@theme` in CSS and names gradients `bg-linear-to-*`; v3 uses `tailwind.config` and `bg-gradient-to-*`. Check which one you have.
- CSS modules, plain CSS, styled-components: same idea. Don't add a styling framework to get a gradient.
- Component library (shadcn, MUI, Chakra...): change its theme tokens first, then override per component.

Don't add dependencies.

- Fonts load the way the project already loads fonts (`next/font`, a `<link>`, an `@import`). Google Fonts is fine.
- Icons: lucide if it's installed, otherwise inline SVG in the same style (24 viewBox, stroke 1.5–2, round caps).
- Motion is CSS. A small IntersectionObserver for scroll reveals is fine. Use framer-motion or GSAP only if they're already there.
- If you really think a package is worth it, ask.

Add, don't rewrite. Wrap things, add classes, add small decorative components (`<GlowBlob />`, `.bg-grid`). Don't rebuild a working component from scratch to change how it looks.

## 4. Don't break the app

- **Logic stays.** Routes, data fetching, state, props, event handlers, API calls, form `name`/`action`/`method`, validation. Restructure markup only when the layout needs it, and keep every handler and binding attached.
- **Real content stays.** Rewrite marketing copy as much as you like. Prices, hours, addresses, legal text, docs, product data and user content stay correct and findable.
- **Fake stuff looks fake.** Invented metrics, testimonials and logos must be obviously fictional: made-up companies, absurd numbers, no real brands, no real people. Never present an invented number as a fact about the actual business.
- **Accessibility survives.** Text stays readable over the effects (put a panel behind it if it isn't). Focus states stay visible, alt text and labels stay, semantic elements stay. Decorative elements get `aria-hidden="true"` and `pointer-events: none`.
- **Reduced motion, every mode.** Infinite and scroll-driven animations go inside `@media (prefers-reduced-motion: no-preference)`. Content that fades in on scroll must be visible without JS and without motion: only hide it once JS has run.
- **Responsive.** Check the mobile layout. Blobs and glows cause sideways scroll, so put `overflow-x: clip` on the page wrapper (`clip`, not `hidden`, so sticky still works).
- **No flashing.** Nothing blinks faster than about twice a second.
- **Stay in your lane.** Tests, backend code, build config and CI stay as they are. Styling config (Tailwind config, global CSS, font setup) is fair game.

## 5. Check

- Run what the project has: typecheck, lint, build, tests. Fix what you broke. Don't invent scripts it doesn't have.
- If you can run the dev server and look at the page, do. If you can't, say so.
- Make sure forms still submit, links still go where they went and the nav works on mobile.

## 6. Report

Short: mode, files changed, anything you left alone on purpose, what you ran and whether it passed. A one-line verdict in the spirit of the mode is fine. No essay about the design.
