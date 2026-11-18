# Toolkit

Working snippets for effects that are easy to get wrong. Use the ones the brief calls for; none are required. Translate them to whatever the project uses (Tailwind, CSS modules, styled-components).

Colors come from the brief, never from these snippets. They use these custom properties, so set them once on `:root` (or as Tailwind theme colors: `@theme` in v4, `tailwind.config` in v3): `--bg` page, `--surface` cards, `--fg` text, `--muted` secondary text, `--line` hairlines, `--accent`, `--accent-2`, `--accent-3`.

## Scroll reveal

Every mode. Content stays visible without JS and without motion.

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

Hard staggers siblings with `transition-delay` (60–100ms apart). Max starts from `filter: blur(10px); transform: translateY(40px) scale(.95)`. In React, Vue or Svelte, put the equivalent in one small hook or component used from the root layout, not copied into every component.

## Backgrounds

```css
.bg-grid {
  background-image:
    linear-gradient(to right, var(--line) 1px, transparent 1px),
    linear-gradient(to bottom, var(--line) 1px, transparent 1px);
  background-size: 40px 40px;
  mask-image: radial-gradient(ellipse at top, black 30%, transparent 70%);
}
.bg-dots { background-image: radial-gradient(var(--line) 1px, transparent 1px); background-size: 24px 24px; }
.bg-mesh {
  background:
    radial-gradient(at 15% 20%, color-mix(in srgb, var(--accent) 40%, transparent), transparent 50%),
    radial-gradient(at 85% 10%, color-mix(in srgb, var(--accent-2) 40%, transparent), transparent 50%),
    radial-gradient(at 60% 90%, color-mix(in srgb, var(--accent-3) 40%, transparent), transparent 50%),
    var(--bg);
}
```

Blobs: 400–700px circles in the accents, 20–35% opacity, `filter: blur(100px)`, absolutely positioned, `aria-hidden="true"`, `pointer-events: none`. If they drift, 20–30s `alternate`, inside `prefers-reduced-motion: no-preference`. Put `overflow-x: clip` on the page wrapper or they scroll the page sideways.

Particles: a few dozen absolutely positioned dots with staggered `animation-delay`. CSS only, no canvas engine.

Grain over the whole page:

```css
body::after {
  content: ""; position: fixed; inset: 0; z-index: 100; pointer-events: none; opacity: .06;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='160' height='160'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.8' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
}
```

## Surfaces

```css
.glass {
  background: color-mix(in srgb, var(--surface) 60%, transparent);
  border: 1px solid var(--line);
  backdrop-filter: blur(16px) saturate(140%);
  box-shadow: 0 8px 32px rgb(0 0 0 / .15), inset 0 1px 0 rgb(255 255 255 / .08);
}

.gradient-border {
  border: 1px solid transparent;
  background:
    linear-gradient(var(--surface), var(--surface)) padding-box,
    linear-gradient(135deg, var(--accent), var(--accent-2)) border-box;
}

@property --angle { syntax: '<angle>'; initial-value: 0deg; inherits: false; }
.spin-border {
  border: 1px solid transparent;
  background:
    linear-gradient(var(--surface), var(--surface)) padding-box,
    conic-gradient(from var(--angle), var(--accent), var(--accent-2), var(--accent-3), var(--accent)) border-box;
}
@media (prefers-reduced-motion: no-preference) {
  .spin-border { animation: spin-border 4s linear infinite; }
}
@keyframes spin-border { to { --angle: 360deg; } }

.orb {
  width: 120px; aspect-ratio: 1; border-radius: 50%;
  background:
    radial-gradient(circle at 30% 30%, rgb(255 255 255 / .55), transparent 30%),
    radial-gradient(circle at 50% 50%, var(--accent), color-mix(in srgb, var(--accent) 30%, black) 70%);
  box-shadow: 0 30px 60px -10px color-mix(in srgb, var(--accent) 50%, transparent);
}
```

One-liners:

- Gradient text: `background: linear-gradient(90deg, var(--accent), var(--accent-2)); -webkit-background-clip: text; background-clip: text; color: transparent;`
- Outlined text: `color: transparent; -webkit-text-stroke: 1.5px var(--fg);`
- Highlighter: `background: linear-gradient(transparent 60%, color-mix(in srgb, var(--accent) 45%, transparent) 0);`
- Hard offset shadow: `border: 3px solid var(--fg); box-shadow: 6px 6px 0 var(--fg);` On hover, move it 2px up-left and grow the shadow by the same amount.
- Glowing heading: `text-shadow: 0 0 40px color-mix(in srgb, var(--accent) 50%, transparent);`
- Blinking cursor: `animation: blink 1s steps(1) infinite;` with `@keyframes blink { 50% { opacity: 0; } }`.

## Marquee

```css
.marquee { overflow: hidden; mask-image: linear-gradient(to right, transparent, black 15%, black 85%, transparent); }
.marquee-track { display: flex; gap: 3rem; width: max-content; }
@media (prefers-reduced-motion: no-preference) {
  .marquee-track { animation: marquee 30s linear infinite; }
  .marquee:hover .marquee-track { animation-play-state: paused; }
}
@keyframes marquee { to { transform: translateX(-50%); } }
```

Render the list twice inside the track and mark the second copy `aria-hidden="true"`. A tilted band is the same thing inside a wrapper with `rotate: -3deg`.

## Pointer effects

Attach only for fine pointers with motion allowed, and use passive listeners.

```js
const fancy = matchMedia('(pointer: fine) and (prefers-reduced-motion: no-preference)').matches;

// Cursor follower: a fixed, aria-hidden element with class .cursor-glow
const glow = document.querySelector('.cursor-glow');
if (fancy && glow) addEventListener('pointermove', (e) => {
  glow.style.transform = `translate(${e.clientX}px, ${e.clientY}px)`;
}, { passive: true });

// Spotlight cards
if (fancy) for (const card of document.querySelectorAll('.spotlight')) {
  card.addEventListener('pointermove', (e) => {
    const r = card.getBoundingClientRect();
    card.style.setProperty('--x', `${e.clientX - r.left}px`);
    card.style.setProperty('--y', `${e.clientY - r.top}px`);
  }, { passive: true });
}
```

```css
.cursor-glow {
  position: fixed; left: -200px; top: -200px; width: 400px; aspect-ratio: 1; border-radius: 50%;
  background: radial-gradient(closest-side, color-mix(in srgb, var(--accent) 30%, transparent), transparent);
  pointer-events: none; z-index: 0;
}
.spotlight {
  background:
    radial-gradient(300px circle at var(--x, -999px) var(--y, -999px), color-mix(in srgb, var(--accent) 15%, transparent), transparent 70%),
    var(--surface);
}
```

The glow doesn't have to be a glow: the same follower can be a crosshair with coordinates, a block cursor or a star.

## Parallax

```css
@supports (animation-timeline: scroll()) {
  @media (prefers-reduced-motion: no-preference) {
    .parallax { animation: parallax linear both; animation-timeline: scroll(); }
  }
}
@keyframes parallax { to { transform: translateY(-20vh); } }
```

Without support, a small `requestAnimationFrame` scroll handler, or nothing.
