# Directions

Do this before touching any code. It ends in a short brief that every later choice follows.

Everything below is inspiration, not a recipe. Each row is a look an AI really produces, and none of them is required. What is required: one coherent direction, structurally different from the stock page, still unmistakably generated.

## Process

1. **Decide what's fixed.**
   - The user named something ("brutalist", "keep it light", "green", "bento"): that part is decided. Roll the rest.
   - The site is already slop (gradients, glass, a bento grid): keep its flavor and layout and push them. Roll only the set piece.
   - Otherwise, roll everything.
2. **Roll.** Picked by feel, it comes out the same every time. So run exactly this:

   ```
   od -An -N4 -tu1 /dev/urandom
   ```

   Four numbers from 0 to 255: **A B C D**. Flavor is row `A mod 12`, hero `B mod 10`, page structure `C mod 8`, set piece `D mod 12`.

   If the command won't run, choose each one yourself, away from your first instinct, and not Indigo SaaS unless the site is already purple.
3. **One veto.** If a value fights the site in a way that isn't funny (horizontal rails for three paragraphs of content, a versus table with nothing to compare), take the next row down. A clash that is funny stays. A bike shop rendered as a terminal is the point.
4. **Fill in the rest** (type, nav, surfaces, decoration, motion, voice) so the rolled parts become one thing. Classic takes the calmest option from each menu, hard the louder ones, max the loudest.
5. **Make it this site's.** Translate the subject into the flavor's motifs. A bike shop's orbit is a wheel with spokes. A bakery's pipeline is Mix → Proof → Bake. A dentist's terminal prints `> scheduling cleaning…`. This is what keeps two runs in the same flavor from looking alike.
6. **Write the brief and check it** (bottom of this file).

## Flavors (A)

| # | Flavor | Light/dark, palette | Type | Surfaces and motifs | Signature tell |
|---|---|---|---|---|---|
| 0 | Indigo SaaS | light; white, slate, indigo → violet | Inter or Geist, one family | white cards, wide soft shadows, hairlines, masked grid, top halo | gradient phrase in the headline |
| 1 | Aurora glass | dark; near-black, purple → cyan, some fuchsia | Inter + one italic serif word | frosted glass, blurred blobs, glowing edges, spotlight | "● All systems operational" |
| 2 | Dev-tool noir | dark; black, greys, one accent (electric blue, orange or lime) | Geist or Inter + a mono for labels | 1px hairlines, visible grid lines with `+` at the crossings, light beams, shimmer borders | `[01] FEATURES` in mono, a `⌘K` hint |
| 3 | Warm editorial | light; cream, ink, terracotta or olive | serif display (Instrument Serif, Fraunces, Newsreader) + plain sans | paper cards, rules, grain, `✻` ornaments, hand-drawn underlines | italic serif everywhere, "Thoughtfully crafted" |
| 4 | Neo-brutalist | light; off-white, black, yellow, pink, blue | heavy grotesk (Space Grotesk, Archivo, Bricolage Grotesque) | 2–3px black borders, hard offset shadows, small radius, rotated stickers, stars | a tilted "NEW!" sticker |
| 5 | Pastel mesh | light; peach, lavender, mint mesh gradients | rounded sans (Plus Jakarta Sans, Outfit, DM Sans) | `rounded-3xl`, puffy clay surfaces, soft blobs, emoji in the icon tiles | "Your calm space for…" 🌿 |
| 6 | Trust blue | light with navy bands; white, navy, electric blue, emerald | Manrope, Sora or Inter Tight | stacked cards, checklists, shield and lock icons, fake chart cards | a row of vague trust badges ("Secure", "Private", "Reliable") |
| 7 | Terminal | dark; black, phosphor green or amber | mono everywhere (JetBrains Mono, IBM Plex Mono, Space Mono) | ASCII boxes, `>` prompts, scanlines, `[ bracketed ]` buttons | `> initializing…` typing out with a blinking cursor |
| 8 | Holo Y2K | silver-light or dark; iridescent pink, cyan, lilac, lime, chrome | wide display (Unbounded, Syne) + plain sans | glossy pills, chrome orbs, `✦ ✧` stars, wireframe globe | holographic gradient text |
| 9 | Luxe noir | dark (or ivory); black, champagne gold | thin high-contrast serif (Cormorant, Playfair Display) + tracked caps | hairline gold frames, huge whitespace, roman numerals | "Crafted for the few." |
| 10 | Keynote bento | light grey; `#f5f5f7`, black, white, one vivid accent | Inter Tight or Inter Display, huge and tight | giant rounded tiles, product shots on flat color | one-word headings: "Fast. Beyond." |
| 11 | Acid startup | black or off-white; acid lime or hot orange | chunky grotesk (Bricolage Grotesque, Unbounded) | pills everywhere, 3D blobs, marquee bands, `↗` arrows | "Meet your new [thing] agent ↗" |

## Heroes (B)

| # | Hero | |
|---|---|---|
| 0 | Centered stack | eyebrow, headline, subhead, two buttons, a visual below |
| 1 | Split | copy left; mockup, framed photo or collage of floating chips right |
| 2 | Giant type | headline fills the width, left-aligned; subhead and buttons tucked into a corner |
| 3 | Prompt box | a big fake AI input ("Ask [Name] anything…") with suggestion chips; it's a link or button to the real main action |
| 4 | Device frame | one big framed mockup (browser, phone, window) with the headline above or overlaid |
| 5 | Editorial | asymmetric grid, offset headline, a narrow side column with a date line or an index |
| 6 | Full-bleed | a visual fills the viewport (mesh, photo, pattern); copy sits in a panel at the bottom left |
| 7 | Bands | full-width stacked strips: marquee, headline, stats |
| 8 | Card fan | tilted, overlapping cards around or behind the headline |
| 9 | Console | the headline types out in a terminal or app window; buttons look like commands |

## Page structures (C)

How everything below the hero is laid out. It repeats; that's part of the joke.

| # | Structure | |
|---|---|---|
| 0 | Classic stack | centered label → heading → muted line → grid, every section |
| 1 | Zigzag | rows alternating visual-left and visual-right |
| 2 | Sticky split | heading pinned on the left, items scrolling past on the right |
| 3 | Chapters | numbered full-height sections behind giant numerals |
| 4 | Bento | one big mixed-span grid carries most of the page |
| 5 | Rails | horizontal scroll-snap rows of cards, keyboard-scrollable, fine on mobile |
| 6 | Dashboard | laid out like an app: side rail, panels, widgets |
| 7 | Timeline | one vertical line down the page, sections hanging off its nodes |

## Set pieces (D)

The one component people remember. Each mode file says how big it gets.

| # | Set piece | |
|---|---|---|
| 0 | Logo marquee | "Trusted by" made-up companies, scrolling forever |
| 1 | Metrics band | three or four huge numbers with tiny labels |
| 2 | Product mockup | a fake app window built from divs and SVG: sidebar, chart, rows |
| 3 | Orbit | the logo in the middle, rings, small chips circling it |
| 4 | Pipeline | "How it works" as nodes joined by lines, a dot travelling along them |
| 5 | Versus table | "The old way" against "[Name]", ✗ against ✓ |
| 6 | Testimonial wall | a masonry of quote cards (classic: only with real testimonials) |
| 7 | Stacking cards | cards that pin and stack on top of each other as you scroll |
| 8 | Globe | a dotted globe or map, "Serving [real place] and beyond" |
| 9 | Chat demo | a fake AI conversation answering real questions with real facts, "✦ Thinking…" |
| 10 | Giant wordmark | the name spelled across the full width, usually in the footer |
| 11 | Spotlight grid | cards with a glow that follows the cursor |

## The rest (not rolled)

Pick whatever makes the rolled parts cohere.

- **Type.** One display family and one body family at most, plus a mono if the flavor wants one. Headline treatments: gradient word, italic serif word, highlighter mark, outlined text, chrome, hand-drawn underline, typed with a cursor.
- **Light/dark balance.** All light, all dark, light page with one dark band, dark hero into a light body, inverted final CTA.
- **Nav.** Hairline sticky bar, floating pill, three-part split (logo, pill of links, CTA), announcement strip on top, side rail, a minimal bar with a big "Menu" button.
- **Surfaces.** Soft shadow, glass, gradient border, hard offset shadow, hairline only with corner marks, puffy clay, chamfered corners, tilted stickers, grainy paper, a side-tab accent (`border-l-2`) on lists and quotes.
- **Stock parts.** Logo: a letter or simple glyph in a tile wearing the signature move, then the name. How it works: three numbered steps. Pricing: three tiers, the middle one "Most popular", real prices only. FAQ: `<details>`/`<summary>` with a chevron, no JS. Footer: logo and a one-liner, columns of the links that actually exist, a hairline, `© [year] Name. All rights reserved.`
- **Decoration.** Masked grid or dots, blurred blobs, mesh gradient, grain, beams, `+` marks, orbs, stars, squiggles, wavy dividers, scanlines, floating UI chips.
- **Motion.** Fade-up, blur-in, word-by-word headline, count-up numbers, typewriter, a rotating word in the headline, marquee, tilt or spotlight on hover, shine sweep, slow float, gradient pan.
- **Voice.** SaaS vague ("Everything you need, in one place"), founder hype ("We're building the future of…"), dev terse ("Ship faster."), calm wellness ("Breathe. We've got this."), enterprise trust ("Built for scale."), luxury hush ("Crafted. Not made."), playful emoji ("Say goodbye to 👋 …"), agent-speak ("Your autonomous [thing] copilot"), manifesto ("We believe…").

## The tells

Diversity doesn't mean taste. Whatever the flavor, it has to read as generated. These ten work in any flavor; say each one in the flavor's own vocabulary (the pill badge of Indigo SaaS is a mono tag in Terminal and a sticker in Neo-brutalist):

1. A small label above the main heading.
2. One treated phrase in the headline.
3. The same section rhythm, over and over: label, heading, one muted sentence, grid.
4. A grid of same-template cards: icon in a tile, two-word title, one line each, all the same length.
5. Fade-up on scroll.
6. A decorative background layer.
7. Line icons (lucide or lookalikes), plus the flavor's sparkle: `✦`, `★`, `✻`, `*`.
8. A closing CTA block that repeats the hero.
9. Copy tics: em dashes, "Not just X. Y.", "Simplify. Automate. Scale.", "so you can focus on what matters".
10. Fictional social proof: made-up company logos, or testimonials (rules in the mode file).

The mode file says how many and how loud.

## One direction, three intensities

Higher modes push the same flavor further. They don't swap it for a darker one or paste in other flavors' parts.

| Flavor | classic | hard | max |
|---|---|---|---|
| Indigo SaaS | White, one indigo → violet phrase, three soft cards, faint grid. | Gradient on every section, gradient-bordered cards, a mockup with chips bobbing around it, metrics band, marquee. | Gradients in gradients in gradients, rotating borders on every card, six bobbing chips, "300% More Future". |
| Warm editorial | Cream, a serif headline with one italic word, a ruled three-column list. | Grain, `✻` before every heading, hand-drawn circles around words, pull quotes, word-by-word reveals. | An "Issue Nº 2026" masthead, drop caps everywhere, a manifesto, a blurb from a fictional critic, footnotes on the footnotes. |
| Terminal | Black, mono, `>` labels, bracketed buttons, one still ASCII frame. | The headline types itself, blinking cursor, scanlines, a fake log scrolling `[ok] wheel trued`, green glow. | ASCII-art logo, a boot log beside the hero, every card its own window running a fake process, `sudo book --repair`. |
| Neo-brutalist | Off-white, black borders, one yellow accent, a single sticker. | Stickers on every section, offset shadows that jump on hover, a tilted marquee band, stars. | Three crossing marquee bands, everything rotated a degree or two, stickers on stickers, "WOW!" bursts. |

## The brief

Write it down before editing anything (working notes are enough), then follow it:

```
Mode:       hard
Flavor:     Neo-brutalist. Off-white, black, yellow #ffe14d, pink #ff6b9a
Hero:       Giant type, left-aligned, sticker cluster top right
Structure:  Chapters 01–04 behind giant outlined numerals
Set piece:  Versus table, "Other bike shops" ✗ vs "Lowgear" ✓
Type:       Bricolage Grotesque 800 for headings, Inter for body
Surfaces:   3px black borders, 6px 6px 0 shadows, radius 8px
Decoration: stars, halftone dots, a tilted marquee band
Motion:     fade-ups, stickers wobble on hover, marquee
Voice:      playful founder. "Fixing bikes. Loudly."
This site:  stars shaped like spoked wheels, prices as ticket stubs
```

Check it:

- **Coherent.** Could one prompt have produced every line? One palette, one signature move, motifs that belong together.
- **Different.** The hero and section layout differ from the stock centered-hero-three-cards page, unless that's what you rolled. New colors on the stock layout is not a direction.
- **Generated.** The tells are there. If it looks like a studio with opinions made it, it's too good. Add tells.
- **Not a clone.** A genre, never a copy of a specific real company's site, logo or wording.
