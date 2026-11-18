# Max

The brief with the restraint taken out. Every AI landing page in that flavor merged into one, and nobody stopped it. This is the screenshot mode.

It's still a website. The nav works, text is readable, forms submit, the real info can be found. The joke is recognizable patterns pushed much too far, not random noise.

Max is not hard plus every component from every flavor. It's this flavor with no ceiling: its signature move on everything, its motifs multiplying, its voice turned into parody. A neo-brutalist max is a riot of stickers and marquee bands, not a glass dashboard. A warm editorial max is an insufferable magazine, not a neon arcade. Take the loudest option from every menu, then exaggerate it.

## Intensity

- **Tells.** All ten, each exaggerated into a parody of itself. Several labels stacked over the headline ("✦ AI-powered", "NEW", "v4.0 — now with more future"). Three treatments in one headline, like a mono line above it (`// the future of the future`), an italic serif word and a gradient word, or the flavor's equivalents. The card grid in every section. The sparkle on almost every heading, some of them twinkling.
- **Signature move on everything**, including where it doesn't belong: inputs, the footer, the scrollbar, the focus ring (still visible). Gradient text in gradient cards in gradient sections, if gradients are the move. If the flavor glows, the headings glow.
- **Decoration.** Every layer the flavor has, at once. Floating shapes around every section in its vocabulary: orbs and rings, stickers and stars, ornaments, ASCII glyphs, chrome blobs. Huge low-opacity numerals (`01`, `02`) behind section headings.
- **Set pieces.** The rolled one at ridiculous scale, plus at least three more, nested: a bento inside a bento cell, an orbit inside the mockup, a marquee inside a card. Every visualization, none of them meaning anything.
- **Hero.** Bigger than reasonable. The label stack, the headline, a subhead, three CTAs competing for attention ("Get started", "Book a demo", "Watch the future ▶"), a visual with too many widgets orbiting it, metrics underneath.
- **Sections that make no sense.** At least one: "Why the future chose us", "The benefits of benefits", "Our approach to approaches".
- **Final CTA.** More dramatic than the hero: full viewport, the biggest text on the page, the flavor's loudest effect, three buttons, "The future isn't coming. It's already here."

## Motion

- Loops wherever the flavor allows: drifting, marquees, pulsing dots, blinking cursors, typewriters, rotating headline words, orbits, dots travelling along lines, floating, shimmer.
- Hovers lift, glow, tilt and shine. `scroll-behavior: smooth` on `html`.
- Overdramatic staggered reveals in the flavor's manner: from `blur(10px) scale(.95) translateY(40px)` to sharp, brutalist blocks slamming in with an overshoot, terminal lines typing in, editorial words fading in one at a time.
- Parallax on decorative layers. CSS scroll-driven animation inside `@supports` first, a small `requestAnimationFrame` handler otherwise.
- A cursor follower in the flavor's style: a soft glow, a crosshair with coordinates, a trail of fading stars, a block cursor. `(pointer: fine)` only, passive listeners.
- Magnetic primary buttons that lean a few pixels toward the cursor.
- Things rotate, bounce, float, pulse and blink.

Reduced motion still wins. Under `prefers-reduced-motion: reduce` everything stops and the JS effects don't attach. Nothing flashes faster than twice a second.

Max should look terrible, not run terribly. Animate `transform` and `opacity`, keep the number of huge blurred layers sane, and use `will-change` only on things that move constantly.

## Copy

Overuse everything, in the brief's voice turned into parody.

- Em dashes — everywhere — constantly.
- "Not X. Y." "More than X. It's Y." "This isn't just X. It's a revolution." "Stop doing X. Start doing Y." "The future isn't coming. It's already here." "One platform. Endless possibilities." "Your imagination is the only limit."
- Headlines: "The future of the future is here." "One platform. Infinite everything." "Not just automation. A revolution in possibility." "Your entire universe, reimagined." "Unlock the next generation of next-generation technology."
- The voice at max: luxe says "An heirloom-grade repair ritual, for the few who truly ride." Wellness says "Breathe in. Ride out. Transcend." A terminal says `> rm -rf limitations`.
- Every buzzword (seamless, revolutionary, next-generation, AI-powered, effortless, transformative, supercharge, elevate, reimagine, unlock, orchestrate), then the meaningless technical ones: neural, quantum, hyperscale, agentic, mesh, orchestration layer, latent, zero-shot.
- Say everything three times: heading, subheading, button.

## Invented stuff

Absurd and unmistakably fake:

- Metrics: `1000x Synergy · ∞ Productivity · 99.99% Innovation · 10,000+ Visionary Teams · 0% Friction · 300% More Future`.
- Features become fictional products, with the real feature readable underneath. "Flat tire repair" becomes "TireSync™ — neural pressure orchestration", and the description still says it's a flat fix, $15, about 20 minutes.
- Testimonials are obvious parody. "I used to have problems. Now I have solutions." — Chad Vision, Chief Future Officer, Synergex. Five glowing stars.

The facts still survive. The prices are still the prices, even when the section is called "Investment Tiers for the Mobility Singularity". Someone who knows what they're looking for should find it in a few seconds.
