# Classic

Believable slop. What you get when you ask for "a modern SaaS landing page" and nothing else. Nobody would look twice at it, which is the point.

Light, clean, purple-blue, centered, safe.

## Type

- Inter. Geist if it's a Next.js project. One family for everything; hierarchy comes from size and weight.
- Hero headline: huge and tight. Around `text-5xl md:text-7xl font-semibold tracking-tight leading-[1.05]`, twelve words at most. Highlight one phrase with gradient text: `bg-gradient-to-r from-indigo-500 to-violet-500 bg-clip-text text-transparent`.
- Subhead: `text-lg md:text-xl text-slate-600 max-w-2xl mx-auto`.
- Section headings: `text-3xl md:text-5xl font-semibold tracking-tight`, centered, short grey paragraph underneath.
- Tiny section labels above headings: `text-xs font-medium uppercase tracking-widest text-indigo-600`. Number them: `01 — Features`.

## Color

- Background white or `#fafafa`. If the site is already dark, keep it dark (`slate-950`) and use the same accents.
- Text `slate-900`, muted `slate-500`/`slate-600`.
- Accent indigo/violet (`#6366f1`, `#8b5cf6`), blue (`#3b82f6`) for gradient stops.
- Gradients go indigo → violet or blue → purple. Put one on the highlighted headline phrase, the primary button, the final CTA panel and a background halo. Then find somewhere else to put another one.
- Borders are hairlines: `border-slate-200/70`, or `rgba(15, 23, 42, .08)`.
- Shadows are wide and soft: `0 1px 2px rgba(0,0,0,.04), 0 12px 32px -12px rgba(15,23,42,.12)`. The primary button gets a colored one: `shadow-lg shadow-indigo-500/25`.
- Radius: `rounded-2xl` on cards, `rounded-full` or `rounded-xl` on buttons and badges.

## Background

A soft halo behind the hero, `radial-gradient(60% 50% at 50% 0%, rgba(99,102,241,.15), transparent)`, and a faint grid that fades out:

```css
.bg-grid {
  background-image:
    linear-gradient(to right, rgba(15, 23, 42, .05) 1px, transparent 1px),
    linear-gradient(to bottom, rgba(15, 23, 42, .05) 1px, transparent 1px);
  background-size: 40px 40px;
  mask-image: radial-gradient(ellipse at top, black 30%, transparent 70%);
}
```

Dots work too: `radial-gradient(rgba(15,23,42,.08) 1px, transparent 1px)` at `24px 24px`.

## Layout

Everything centered in `max-w-6xl` or `max-w-7xl`. Every section gets the same generous padding (`py-24 md:py-32`) and the same rhythm: label, heading, paragraph, grid.

The default page, top to bottom:

```
Navbar → Hero → Logo cloud → Features → How it works → Testimonials → Pricing → FAQ → Final CTA → Footer
```

Map existing content onto it instead of inventing content. A services list is the features grid. A price list is pricing. Opening hours and "do I need an appointment" make a perfectly good FAQ. Skip sections that have nothing real to put in them.

## Components

**Navbar.** Sticky, `bg-white/80 backdrop-blur border-b border-slate-200/70`. Logo on the left: a small gradient rounded square with a letter or simple mark, then the name. Links in the middle, optionally inside a pill (`rounded-full border px-2 py-1`). One CTA on the right.

**Hero.** Centered. A pill eyebrow above the headline: `rounded-full border bg-white px-3 py-1 text-sm text-slate-600`, with a tiny "New" chip and a `→`. Then headline, subhead, two buttons side by side.

**Buttons.** Primary: indigo-violet gradient or solid indigo, white text, colored shadow, a `→` that nudges right on hover. Secondary: white, hairline border, same size.

**Feature cards.** Three columns, stacked on mobile, three or six cards. All nearly identical: `rounded-2xl border bg-white p-6 shadow-sm`, an icon tile (`size-10 rounded-xl bg-indigo-50 text-indigo-600 grid place-items-center`), a two-word title, one or two lines of description. Make the descriptions the same length.

**How it works.** Three steps. Big light numbers (`01 02 03`) in the accent color, a dashed line connecting them on desktop.

**Logo cloud.** "Trusted by teams at" and five or six grey wordmarks set in text, with different weights and letter-spacing so they read as logos. Fictional companies only.

**Testimonials.** Restyle the ones that exist: card, quote, gradient circle with initials, name, role. Classic doesn't invent testimonials. Hard does.

**Pricing.** Three tiers, the middle one highlighted with a "Most popular" badge, an indigo ring and a little extra scale. Real prices only. If the thing doesn't sell anything, there's no pricing section.

**FAQ.** `<details>`/`<summary>` with a chevron. No JS needed.

**Final CTA.** A `rounded-3xl` indigo → violet panel, white heading, one sentence, two buttons.

**Footer.** Logo and a one-liner, three or four columns of the links that actually exist, a hairline, `© 2026 Name. All rights reserved.`

**Images.** Keep real photos and product shots; give them `rounded-2xl`, a ring and a soft shadow. Decorative stock photos can become abstract SVG: overlapping circles, soft blurred shapes, a gradient mesh.

## Motion

- Fade up on scroll: opacity 0 → 1, `translateY(16px)` → 0, about 600ms ease-out, once.
- Hover: cards get a slightly bigger shadow, buttons darken, arrows nudge.
- Nothing loops. Infinite animation starts at hard.

For a plain site:

```css
@media (prefers-reduced-motion: no-preference) {
  .js .reveal { opacity: 0; transform: translateY(16px); transition: opacity .6s ease-out, transform .6s ease-out; }
  .js .reveal.is-visible { opacity: 1; transform: none; }
}
```

```js
document.documentElement.classList.add('js');
const io = new IntersectionObserver((entries) => {
  for (const e of entries) if (e.isIntersecting) { e.target.classList.add('is-visible'); io.unobserve(e.target); }
}, { threshold: 0.15 });
document.querySelectorAll('.reveal').forEach((el) => io.observe(el));
```

In React, Vue or Svelte, put the equivalent in one small hook or component used from the root layout, not copied into every component.

## Copy

Confident, vague, could describe any product.

- Headlines: "Your [thing], reimagined." "Everything you need to [verb], in one place." "Unlock the power of [thing]." "From chaos to clarity." "Meet the next generation of [thing]." "Built for the future." "Simplify. Automate. Scale." "Less complexity. More possibility."
- Subhead: "[Name] helps [people] [do the real thing] — so you can focus on what matters."
- "Not just X. Y." Once or twice per page.
- Feature titles are adjective + noun: "Lightning-fast setup", "Seamless integrations", "Built-in insights". Descriptions are one sentence that says nothing specific.
- Em dashes. A couple per section.
- Buttons: "Get started", "Start for free", "Book a demo", "Learn more →".
- Stay believable. No "revolutionary", no absurd numbers. That's hard mode.
- If you need a stats row and there are no real numbers, use ones that claim nothing ("24/7", "3 steps") or come from the content ("since 2011", "12 services"). Don't invent customer counts in classic.

The facts survive the rewrite. "We fix flats in 20 minutes, $15" can become "Flat to fast — in 20 minutes." The price stays $15.
