# Hard

The brief after someone asked for "more premium, modern, futuristic and AI-powered" five times in a row. Obvious slop. Still works.

Hard is the same kind of direction pushed until nobody could mistake it for a person's work: more effects, more clichés, complexity nobody asked for. It is not "classic, but dark". A light flavor at hard is light and loud. Take the louder options from every menu, all inside the flavor.

## Intensity

- **Tells.** All ten, loud.
- **Signature move everywhere.** The flavor's trick goes on the nav, the hero, every heading, the cards, the buttons and the footer. Then it nests: a gradient card in a gradient section holding a gradient button, a sticker on a stickered card, a window inside a window.
- **Decoration.** Two or three layers per screen, from the flavor's vocabulary: blobs and grid, grain and ornaments, scanlines and ASCII, stars and halftone. Something decorative next to every heading.
- **Set pieces.** The rolled one, big and moving. Plus two more from the set-piece list that suit the flavor.
- **Unnecessary complexity.** A mockup or diagram that explains very little, with small widgets floating around it ("+38% this week ↑", "✦ AI suggestion", a toggle). A metrics band. Somewhere, a grid with mixed spans. The CTA three times (after the hero, mid-page, at the end), worded slightly differently each time.
- **Type.** The hero headline goes up a size (`text-6xl md:text-8xl` or the flavor's equivalent) and gets two treatments: italic serif word plus gradient word, outlined word plus highlighter, typed line plus glow. Every section heading gets an eyebrow: "✦ AI-powered", "Next-generation", "Introducing".
- **Nav.** Showier than a plain bar: a floating pill, a three-part split, an announcement strip above it, a pulsing "● All systems operational" dot.

## Motion

On top of the fade-ups:

- Stagger children by 60–100ms.
- Three to five loops that fit the flavor: drifting blobs, a marquee, pulsing status dots, a blinking cursor (1s, `steps(1)`), a typewriter line, a rotating word in the headline, an orbit, a dot travelling along a line, slow floating, a shimmer or gradient pan.
- Hover: cards lift and react in the flavor's way (glow, offset shadow grows, border brightens, slight tilt). Buttons scale a touch (`1.02`); primary ones get a shine sweeping across.
- `scroll-behavior: smooth` on `html`.

Every infinite animation lives inside `prefers-reduced-motion: no-preference`.

## Copy

The tics from the tells (em dashes, "Not just X. Y.", tricolons), louder, in the brief's voice. Use these until it hurts: seamless, revolutionary, next-generation, AI-powered, intelligent, effortless, powerful, transformative, innovative, scalable, future-ready, supercharge, elevate, reimagine, unlock, orchestrate.

- "Supercharge your [thing]." "The future of [thing] starts here." "One platform. Infinite possibilities." "Seamlessly connect everything." "Go beyond [thing]." "Your entire [thing]. Finally unified." "10x faster. Zero friction." "Built for teams that build the future."
- Bend them to the voice. Calm wellness says "Effortlessly mindful. Intelligently calm." A terminal says `> deploying next-gen repairs…`. Luxe says "Elevating excellence, effortlessly."
- Prefix feature names with "AI-powered" or "Intelligent". Say everything twice: a heading, a subheading that restates it, a button that restates it again.
- The flavor's sparkle (`✦`, `★`, `✻`, `*`) next to anything that could be described as AI.

## Invented stuff

- Metrics are marketing nonsense, not claims about the business: "10x faster", "0 friction", "∞ scale", "100% next-gen".
- No testimonials? Add three generic ones with obviously fictional names and companies ("Jordan Lee, Head of Ops at Initech"), five stars.
- Mockup data is decoration and can be fake.

The real facts still survive.

If your hard result could pass for classic, you held back. If all that changed is that it went dark, you held back in a different way.
