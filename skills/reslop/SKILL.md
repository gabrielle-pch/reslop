---
name: reslop
description: Restyle an existing frontend so it looks AI-generated on purpose. Each run rolls a fresh flavor of slop (indigo SaaS, aurora glass, dev-tool noir, warm editorial, neo-brutalist, terminal and more) and applies it at one of three intensities, classic, hard or max. Plus a read-only slop score. Use when the user runs /reslop or explicitly asks to make their site look AI-generated or "reslopped". Not for normal design work.
argument-hint: "[classic|hard|max|score] [extra notes]"
# lets it read its own reference files and roll its dice without a permission prompt
allowed-tools: Read(/${CLAUDE_SKILL_DIR}/references/**), Bash(od -An -N4 -tu1 /dev/urandom)
---

# Reslop

Make the site look like Claude built it in one prompt.

There's more than one way that goes. The white page with an indigo gradient phrase and three icon cards. The black dev-tool page with mono labels and light beams. The cream page with an italic serif in every heading. The neo-brutalist page with a tilted "NEW!" sticker. You know them all. Each run picks one fresh and commits to it: many flavors of slop, not one template with a volume knob.

The joke only works if the app still works. We're ruining the design, not the code.

## Pick a mode

Input: `$ARGUMENTS`

| Input | Mode | Read, in order |
|---|---|---|
| nothing, or `classic` | classic | `directions.md`, `classic.md`, `toolkit.md` |
| `hard` | hard | `directions.md`, `hard.md`, `toolkit.md` |
| `max` | max | `directions.md`, `max.md`, `toolkit.md` |
| `score` | score | `score.md` only. Don't edit anything. |

The files live in `${CLAUDE_SKILL_DIR}/references/`.

Modes are intensity, not style. The look (palette, type, layout, motifs) comes from the direction you pick in step 2. The mode decides how far you push it:

- **classic**: believable, generic, slightly soulless. It could ship and nobody would look twice.
- **hard**: obviously AI-generated. More effects, more clichés, complexity nobody asked for.
- **max**: absurdly overengineered. Every embellishment the direction allows, then more.

Higher modes push the same direction further. They don't paste in the lower mode's components, and hard doesn't mean dark.

Anything after the mode word is extra instructions (`/reslop max but leave the docs pages alone`, `/reslop hard brutalist`, `/reslop classic but keep it light`). Follow them. If they name a flavor, palette or layout, that replaces the roll for that part. If the user asked in plain words instead of a command, pick the closest mode. "Go all the way" means max.

Each mode has to look different in a screenshot, and so do two runs. If your hard result could pass for classic, you held back. If recoloring it indigo would give you the stock centered-hero-three-cards page (and that's not what you rolled), you only changed the paint.

## 1. Look first

- **Git.** If there are uncommitted changes, stop and ask before going further. Reslop touches a lot of files and people will want a clean undo.
- **Stack.** Read `package.json` (or whatever the project has) and the config files. Framework, router, how styles are written (Tailwind v3 or v4, CSS modules, plain CSS, styled-components, a component library), where global styles and theme tokens live, how fonts load.
- **What it is.** Read the main pages. A bike shop stays a bike shop. It just becomes "the AI-native platform for your ride". Real names, prices, hours, product data and docs stay.
- **What it looks like.** Current colors, fonts, light or dark, how dense, how much personality. Step 2 needs it.
- **What's visible.** Layout shell, navbar, landing page, cards, buttons, footer. That's where the change shows. Settings pages and admin tables get the theme and not much else.
- **Current slop level.** If it already wears a flavor of slop (gradients, glass, a bento grid), keep that flavor and push it. Don't reset it to plain first.

## 2. Pick a direction

Before editing anything, follow `directions.md`: roll a flavor, a hero, a page structure and a set piece, fit them to this site, and write a short brief. Every later choice (font, radius, icon tile, hover, headline) comes from the brief, not from habit. The purple page is one possible outcome, not the fallback.

## 3. Change things in this order

Highest visual impact first, so the screenshot changes even if you run out of steam.

1. **Theme.** Fonts, colors, background, radius, shadows from the brief. One edit to the global CSS or Tailwind theme does half the job.
2. **Navbar.**
3. **Hero.** The rolled composition: headline, eyebrow, buttons, background effects.
4. **Sections and cards.** The rolled structure and set piece: features, lists, pricing, testimonials, footer.
5. **Small stuff.** Buttons, badges, inputs, links, focus rings.
6. **Decoration and motion.**
7. **Copy.**

The direction describes a full landing page. Map existing content onto it instead of inventing content. A services list is the feature grid. A price list is pricing. Opening hours and "do I need an appointment" make a perfectly good FAQ. Skip sections that have nothing real to put in them; if nothing is for sale, there's no pricing. If the project is an app rather than a marketing site (dashboard, tool, docs), restyle what's there and give its headers and empty states the marketing treatment. Don't bolt a pricing section onto a todo app. Max gets more leeway here.

Keep real photos and product shots, framed in the flavor's style. Decorative stock photos can become abstract SVG in the same style.

## 4. House rules

Use what the project already uses.

- Tailwind: write Tailwind. Arbitrary values (`bg-[radial-gradient(...)]`) are fine. Keyframes and anything gnarly go in the global CSS file. v4 sets the theme with `@theme` in CSS and names gradients `bg-linear-to-*`; v3 uses `tailwind.config` and `bg-gradient-to-*`. Check which one you have.
- CSS modules, plain CSS, styled-components: same idea. Don't add a styling framework to get a gradient.
- Component library (shadcn, MUI, Chakra...): change its theme tokens first, then override per component.

Don't add dependencies.

- Fonts load the way the project already loads fonts (`next/font`, a `<link>`, an `@import`). Google Fonts is fine.
- Icons: lucide if it's installed, otherwise inline SVG in the same style (24 viewBox, round caps, stroke 1.5–2.5 to suit the flavor).
- Motion is CSS. A small IntersectionObserver for scroll reveals and a few lines for pointer effects are fine. Use framer-motion or GSAP only if they're already there.
- If you really think a package is worth it, ask.

Add, don't rewrite. Wrap things, add classes, add small decorative components (`<GlowBlob />`, `.bg-grid`). Don't rebuild a working component from scratch to change how it looks.

## 5. Don't break the app

- **Logic stays.** Routes, data fetching, state, props, event handlers, API calls, form `name`/`action`/`method`, validation. Restructure markup only when the layout needs it, and keep every handler and binding attached.
- **Real content stays.** Rewrite marketing copy as much as you like. Prices, hours, addresses, legal text, docs, product data and user content stay correct and findable.
- **Fake stuff looks fake.** Invented metrics, testimonials and logos must be obviously fictional: made-up companies, absurd numbers, no real brands, no real people. Never present an invented number as a fact about the actual business. Mockups can hold demo data; in an actual app, real data never gets swapped for demo data.
- **Decoration traps nobody.** A fake prompt box or `⌘K` pill is a link or button to something real, never a dead form field. A fixed or floating nav gets top padding so it covers nothing, and the mobile menu still opens and closes. If there's a light/dark toggle, both themes keep working; the brief picks the default.
- **Accessibility survives.** Text stays readable over the effects (put a panel behind it if it isn't). Focus states stay visible, alt text and labels stay, semantic elements stay. Decorative elements get `aria-hidden="true"` and `pointer-events: none`.
- **Reduced motion, every mode.** Infinite and scroll-driven animations go inside `@media (prefers-reduced-motion: no-preference)`. Content that fades in on scroll must be visible without JS and without motion: only hide it once JS has run.
- **Responsive.** Check the mobile layout. Blobs and glows cause sideways scroll, so put `overflow-x: clip` on the page wrapper (`clip`, not `hidden`, so sticky still works).
- **No flashing.** Nothing blinks faster than about twice a second.
- **Stay in your lane.** Tests, backend code, build config and CI stay as they are. Styling config (Tailwind config, global CSS, font setup) is fair game.

## 6. Check

- Run what the project has: typecheck, lint, build, tests. Fix what you broke. Don't invent scripts it doesn't have.
- If you can run the dev server and look at the page, do. If you can't, say so.
- Make sure forms still submit, links still go where they went and the nav works on mobile.

## 7. Report

Short: mode, the direction in one line (`Neo-brutalist · giant-type hero · chapters · versus table`), files changed, anything you left alone on purpose, what you ran and whether it passed. A one-line verdict in the spirit of the mode is fine. No essay about the design.
