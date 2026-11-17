# Slop score

Read-only. Don't edit anything.

A fixed checklist. Each pattern is worth some points, and the score is the sum of the ones you can point at. If you can't name the file where you saw it, it doesn't count. You're scoring the source, not the pixels, so don't claim anything about how the page looks unless you actually looked at it running.

Look at the styles, markup, components and copy of the user-facing pages. Skip `node_modules`, build output, tests and this skill.

| Pattern | Pts | Counts when you find |
|---|---|---|
| Purple gradients | 10 | a gradient using purple, violet, indigo or fuchsia (Tailwind names, or hex/hsl in that range) |
| Gradient text | 8 | `bg-clip-text` + `text-transparent`, or `background-clip: text` |
| Glassmorphism | 8 | `backdrop-blur` / `backdrop-filter` on a translucent surface |
| Buzzword copy | 8 | three or more of: seamless, supercharge, unlock, reimagine, next-generation, AI-powered, effortless, transform, elevate, revolutionary |
| Inter or Geist | 6 | either loaded or set as the main font |
| Glow blobs | 6 | big blurred decorative elements (`blur-3xl`, `filter: blur(60px)` or more) |
| Pill eyebrow | 6 | a small `rounded-full` label directly above a main heading |
| Identical cards | 6 | a 3-column grid of icon + title + text cards built from one template |
| Floating or pill navbar | 6 | fixed/sticky nav that is `rounded-full` or inset from the edges |
| Big metrics | 6 | a row of big numbers with tiny labels (10x, 99.9%, 10k+) |
| Scroll reveals | 5 | IntersectionObserver reveals, `whileInView`, AOS or similar |
| Infinite marquee | 5 | an infinite `translateX` animation on a row of logos or items |
| Sparkles | 4 | ✦, ✨ or a sparkle icon |
| Lucide icons | 4 | lucide imports, or inline SVG icons in its style sitting in rounded tiles |
| Grid or dot background | 4 | a repeating line or dot pattern used as decoration |
| Italic serif accent | 4 | a serif italic word inside a sans-serif heading |
| Em dashes and "Not just X" | 4 | three or more em dashes in marketing copy, or a "Not just X. Y." line |

That's 100.

| Score | Verdict |
|---|---|
| 0–19 | Made by a human. Possibly with a pencil. |
| 20–44 | Lightly seasoned. Could be a template. |
| 45–69 | Generic SaaS. Your visitors have seen this site before. |
| 70–89 | Almost indistinguishable from a one-shot Claude landing page. |
| 90–100 | Peak slop. Nothing left to add. Run `/reslop max` anyway. |

Report it like this, every row, hits first:

```
RESLOP ANALYSIS

Slop Score: 64/100

✓ Purple gradients      10   app/page.tsx:42
✓ Gradient text          8   app/page.tsx:18
✓ Inter or Geist         6   app/layout.tsx:3
...
✗ Infinite marquee       0
✗ Italic serif accent    0

Verdict: Generic SaaS. Your visitors have seen this site before.
```

If you only read code and didn't render anything, add one line saying so.
