# Max

Classic plus hard, then take the restraint out. Every AI landing page on the internet merged into one, and nobody stopped it. This is the screenshot mode.

It's still a website. The nav works, text is readable, forms submit, the real info can be found. The joke is recognizable patterns pushed much too far, not random noise.

## Color and surfaces

- Purple, cyan and pink (`#a855f7`, `#22d3ee`, `#ec4899`) on near-black, with some indigo. That's the whole palette, used everywhere.
- Every major component gets a gradient. Gradient text in gradient cards in gradient sections. Buttons get a gradient and a gradient glow.
- Glass on everything, with neon edges: `box-shadow: 0 0 0 1px rgba(168,85,247,.5), 0 0 24px rgba(168,85,247,.35), 0 0 80px -20px rgba(34,211,238,.4)`.
- Big headings glow: `text-shadow: 0 0 40px rgba(168,85,247,.5)`.

## Background

Layer all of it: grid, dots, slow particles, four to six giant blobs (purple, cyan, pink), a conic gradient rotating behind the hero, a radial spotlight. Thin diagonal lines if there's room.

Floating shapes around every section: glossy spheres, rings, plus signs, sparkles. A sphere is two radial gradients:

```css
.orb {
  width: 120px; aspect-ratio: 1; border-radius: 50%;
  background:
    radial-gradient(circle at 30% 30%, rgba(255,255,255,.55), transparent 30%),
    radial-gradient(circle at 50% 50%, #a855f7, #3b0764 70%);
  box-shadow: 0 30px 60px -10px rgba(168, 85, 247, .5);
}
```

Particles are a few dozen absolutely positioned dots with staggered `animation-delay`. CSS only, no canvas engine.

## Type

- Three styles in one headline: gradient Inter, italic serif, and a monospace label. `// the future of the future` in mono above "Don't just *innovate.* Transcend." with "Transcend." in gradient.
- Several eyebrow badges over the hero headline at once: "✦ AI-powered", "NEW", "v4.0 — now with more future".
- Huge decorative numbers (`01`, `02`) behind section headings, gradient, low opacity.
- Sparkles next to almost every heading. Some of them twinkle.

## Components

**Hero.** Bigger than reasonable. The badge stack, the headline, a subhead, three CTAs competing for attention ("Get started", "Book a demo", "Watch the future ▶"), hard's fake dashboard with more widgets orbiting it, metrics underneath.

**Metrics.** Absurd and unmistakably fake:

```
1000x Synergy · ∞ Productivity · 99.99% Innovation · 10,000+ Visionary Teams · 0% Friction · 300% More Future
```

**Bento.** Bento grids nested inside bento cells. Every cell has a visualization. None of them mean anything.

**Features.** Rename them as fictional products with absurd names, and keep the real feature readable underneath. "Flat tire repair" becomes "TireSync™ — neural pressure orchestration", and the description still says it's a flat fix, $15, about 20 minutes.

**Sections that make no sense.** At least one: "Why the future chose us", "The benefits of benefits", "Our approach to approaches".

**Testimonials.** Obvious parody. "I used to have problems. Now I have solutions." — Chad Vision, Chief Future Officer, Synergex. Five glowing stars.

**Diagrams.** More of them. Orbits with several rings, nodes everywhere, lines pulsing between them.

**Cards.** A rotating gradient border on most of them:

```css
@property --angle { syntax: '<angle>'; initial-value: 0deg; inherits: false; }
.neon-card {
  border: 1px solid transparent;
  background:
    linear-gradient(#0b0b12, #0b0b12) padding-box,
    conic-gradient(from var(--angle), #a855f7, #22d3ee, #ec4899, #a855f7) border-box;
}
@media (prefers-reduced-motion: no-preference) {
  .neon-card { animation: spin-border 4s linear infinite; }
}
@keyframes spin-border { to { --angle: 360deg; } }
```

Plus floating cards, bouncing icons and slowly rotating shapes.

**Final CTA.** More dramatic than the hero: full viewport, the biggest text on the page, a rotating conic glow, orbs, three buttons, "The future isn't coming. It's already here."

## Motion

Everything from hard, plus:

- Overdramatic reveals: from `blur(10px) scale(.95) translateY(40px)` to sharp, staggered.
- Parallax on blobs and floating shapes. Prefer CSS scroll-driven animation (`animation-timeline: scroll()` inside `@supports`), otherwise a small `requestAnimationFrame` scroll handler.
- A big soft glow that follows the cursor, optionally with a short trail of fading dots. A few lines of JS, `(pointer: fine)` only, passive listeners.
- Magnetic primary buttons that lean a few pixels toward the cursor.
- Things rotate, bounce, float, pulse and blink.

Reduced motion still wins. Under `prefers-reduced-motion: reduce` everything stops and the JS effects don't attach. Nothing flashes faster than twice a second.

Max should look terrible, not run terribly. Animate `transform` and `opacity`, keep the number of huge blurred layers sane, and use `will-change` only on things that move constantly.

## Copy

Overuse everything.

- Em dashes — everywhere — constantly.
- "Not X. Y." "More than X. It's Y." "This isn't just X. It's a revolution." "Stop doing X. Start doing Y." "The future isn't coming. It's already here." "One platform. Endless possibilities." "Your imagination is the only limit."
- Headlines: "The future of the future is here." "One platform. Infinite everything." "Not just automation. A revolution in possibility." "Your entire universe, reimagined." "Unlock the next generation of next-generation technology."
- Meaningless technical words: neural, quantum, hyperscale, agentic, mesh, orchestration layer, latent, zero-shot.

The facts still survive. The prices are still the prices, even when the section is called "Investment Tiers for the Mobility Singularity". Someone who knows what they're looking for should find it in a few seconds.
