# Hard

Classic, after someone asked for "more premium, modern, futuristic and AI-powered" five times in a row. Obvious slop. Still works.

Everything in classic applies unless this file says otherwise. The big shift: go dark, add glass, add glow, start moving.

## Color

- Dark. Background `#05050a` to `#0a0a12`, text `zinc-100`, muted `zinc-400`, borders `white/10`. Hard and max are always dark. If the app has a light/dark toggle, make dark the default and keep the toggle working.
- Purple → cyan (`#a855f7` → `#22d3ee`), with indigo or fuchsia when you need a third stop.
- Gradients inside gradients: a gradient card in a gradient section, holding a gradient button.

## Glass

Nav, cards, dropdowns, modals, toasts, inputs.

```css
.glass {
  background: rgba(255, 255, 255, .04);
  border: 1px solid rgba(255, 255, 255, .08);
  backdrop-filter: blur(16px) saturate(140%);
  box-shadow: 0 8px 32px rgba(0, 0, 0, .35), inset 0 1px 0 rgba(255, 255, 255, .06);
}
```

## Background

- Two to four big blurred blobs: 400–700px, purple, cyan and indigo at 20–35% opacity, `filter: blur(100px)`, absolutely positioned, drifting slowly (20–30s, `alternate`).
- A spotlight glow behind the hero headline. A softer one behind the product mockup.
- The classic grid or dots on top, masked.
- `overflow-x: clip` on the wrapper, or the blobs will scroll the page sideways.

## Type

- An italic serif for one or two words in each big heading: Instrument Serif, Playfair Display or Fraunces, italic, regular weight. "Work, *reimagined*." The rest stays Inter, with a gradient on another word.
- Hero headline goes up a size: `text-6xl md:text-8xl`.
- Every section heading gets an eyebrow badge: "✦ AI-powered", "Next-generation", "Introducing".

## Components

**Floating pill nav.** `fixed top-4`, centered, `rounded-full`, glass, `w-[min(92%,64rem)]`. Pad the top of the page so it doesn't cover anything. The mobile menu still opens and closes.

**Hero.**
- A badge with a pulsing dot on top: "● Now in public beta", "● All systems operational". Green dot plus an `animate-ping` halo.
- Headline with serif italic and gradient, subhead, two CTAs.
- Under that, a product mockup: a fake browser window (three dots, URL bar reading `app.[name].ai`), glass, glowing border, tilted back a little (`perspective(1200px) rotateX(8deg)`). Inside, a fake dashboard built from divs and SVG: sidebar, line chart, stat tiles, a few rows of demo data.
- Two or three small widgets floating around it, bobbing slowly: "+38% this week ↑", "✦ AI suggestion", a toggle.

The mockup's data is decoration and can be fake. In an actual app, real data never gets swapped for demo data.

**Metrics row.** Three or four huge gradient numbers with tiny labels: "10x faster", "99.99% uptime", "0 friction", "∞ scale". Marketing nonsense, not claims about real customers.

**Logo marquee.** The classic logo cloud, now scrolling forever.

```css
.marquee { overflow: hidden; mask-image: linear-gradient(to right, transparent, black 15%, black 85%, transparent); }
.marquee-track { display: flex; gap: 3rem; width: max-content; }
@media (prefers-reduced-motion: no-preference) {
  .marquee-track { animation: marquee 30s linear infinite; }
  .marquee:hover .marquee-track { animation-play-state: paused; }
}
@keyframes marquee { to { transform: translateX(-50%); } }
```

Render the list twice inside the track, and mark the second copy `aria-hidden="true"`.

**Bento grid.** Turn at least one feature grid into a bento: four to six glass cells with mixed spans (`md:col-span-2`, `md:row-span-2`). Each cell gets a decorative mini-visual that explains very little: an SVG sparkline, a node diagram, progress rings, a fake terminal with a blinking cursor, a chat bubble saying "✦ Thinking…", a toggle.

**Gradient borders** on featured cards (the "Most popular" plan, the big bento cell):

```css
.gradient-border {
  border: 1px solid transparent;
  background:
    linear-gradient(#0b0b12, #0b0b12) padding-box,
    linear-gradient(135deg, #a855f7, #22d3ee) border-box;
}
```

**Side-tab accents.** `border-l-2` in the accent color on list items, quotes and the active nav item.

**Orbit.** Somewhere (hero or an integrations block): the logo in the middle, two rings, small icon chips orbiting slowly.

**Connected nodes.** "How it works" becomes nodes joined by lines, with a dot travelling along them.

**Testimonials.** If there are none, add three generic ones. Obviously fictional names and companies ("Jordan Lee, Head of Ops at Initech"). Glass cards, five stars, side-tab accent.

**CTAs.** Repeat them: after the hero, after the bento, at the end. Same two buttons, slightly different words each time.

**Sparkles.** `✦` or a sparkle icon next to anything that could be described as AI.

## Motion

On top of classic's fade-ups:

- Stagger children by 60–100ms.
- Cards lift on hover (`-translate-y-1`), glow (`0 0 40px -10px rgba(168,85,247,.6)`), border brightens.
- Buttons scale a touch (`hover:scale-[1.02]`); primary ones get a shine sweeping across.
- Pulsing status dots, a blinking cursor (1s, `steps(1)`), a typewriter effect on one line, drifting blobs, rotating orbit, scrolling marquee.
- `scroll-behavior: smooth` on `html`.

Every infinite animation lives inside `prefers-reduced-motion: no-preference`.

## Copy

Classic, louder. Use these until it hurts: seamless, revolutionary, next-generation, AI-powered, intelligent, effortless, powerful, transformative, innovative, scalable, future-ready, supercharge, elevate, reimagine, unlock, orchestrate.

- "Supercharge your [thing]."
- "The future of [thing] starts here."
- "One platform. Infinite possibilities."
- "Seamlessly connect everything."
- "Go beyond [thing]."
- "Your entire [thing]. Finally unified."
- "10x faster. Zero friction."
- "Built for teams that build the future."

Prefix feature names with "AI-powered" or "Intelligent". Say everything twice: a heading, a subheading that restates it, a button that restates it again.

The real facts still survive.
