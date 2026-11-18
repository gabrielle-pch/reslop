# Classic

Believable slop. What you get when you ask for "a modern website" once and ship it. Someone who has seen a hundred AI sites clocks it instantly. Everyone else thinks it's a website.

Classic is the brief at its most restrained: generic, tidy, slightly soulless. The flavor is clear and polite. Take the calmest option from every menu.

## Intensity

- **Tells.** At least six of the ten, quietly. Always these five: the label above the heading, the treated headline phrase, the repeating section rhythm, the same-template card grid, fade-ups.
- **Signature move.** The flavor's one trick (a gradient, an italic serif, an offset shadow, a mono bracket, glass) goes in a few places: the headline phrase, the primary button, the final CTA, one background touch. Then find one more place for it.
- **Decoration.** One background layer, faint, masked so it fades out.
- **Set piece.** The rolled one, done modestly and holding still. A marquee becomes a static logo row, an orbit doesn't turn, a pipeline is a dashed line between numbered steps.
- **Layout.** The rolled hero and structure, executed cleanly. One max width for everything (`max-w-6xl` or `max-w-7xl`), the same generous padding on every section (`py-24 md:py-32`), even gaps.
- **Light or dark.** Whatever the flavor says. If it allows both, the site's current balance decides.
- **Components.** Restyle what exists. No invented sections.

## Type

- The flavor's pairing at sensible sizes. Hierarchy from size and weight.
- Hero headline: big and tight, around `text-5xl md:text-7xl` with tight tracking and leading, twelve words at most. One phrase treated.
- Subhead: `text-lg md:text-xl`, muted, `max-w-2xl`.
- Section headings: `text-3xl md:text-5xl`, a short muted paragraph underneath.
- Labels above headings: small, tracked, in the accent and in the flavor's style (uppercase, small caps, mono). Number them: `01 — Features`.

## Surfaces

- Cards: the flavor's card, three or six of them, three columns, stacked on mobile, all nearly identical. Icon in a tile, a two-word title, one or two lines of description. Make the descriptions the same length.
- One radius everywhere. Hairline borders. Shadows soft, or hard if the flavor is brutalist.
- Nav: the calmest version of the flavor's nav. Sticky, a hairline under it, logo left, links in the middle (maybe inside a pill), one CTA right.
- Primary button wears the signature move, with a `→` that nudges right on hover. The secondary is quiet and the same size.

## Motion

- Fade up on scroll, about 600ms ease-out, once (`toolkit.md`).
- Hover: cards get a slightly stronger shadow or border, buttons darken, arrows nudge.
- Nothing loops. Infinite animation starts at hard.

## Copy

Confident, vague, could describe any business. In the brief's voice, kept polite.

- Headlines to start from: "Your [thing], reimagined." "Everything you need to [verb], in one place." "Unlock the power of [thing]." "From chaos to clarity." "Meet the next generation of [thing]." "Built for the future." "Simplify. Automate. Scale." "Less complexity. More possibility." Write one like these in the brief's voice. "Reimagined" is not mandatory.
- Subhead: "[Name] helps [people] [do the real thing] — so you can focus on what matters."
- "Not just X. Y." Once or twice per page.
- Feature titles are adjective + noun: "Lightning-fast setup", "Seamless integrations", "Built-in insights". Descriptions are one sentence that says nothing specific.
- Em dashes. A couple per section.
- Buttons: "Get started", "Start for free", "Book a demo", "Learn more →", or the voice's equivalent.
- Stay believable. No "revolutionary", no absurd numbers. That's hard.

## Invented stuff

- A stats row with no real numbers behind it uses ones that claim nothing ("24/7", "3 steps") or come from the content ("since 2011", "12 services"). No invented customer counts.
- A logo row of made-up companies is fine.
- Testimonials: restyle the ones that exist. Classic doesn't invent them.

The facts survive the rewrite. "We fix flats in 20 minutes, $15" can become "Flat to fast — in 20 minutes." The price stays $15.
