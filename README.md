# cfa-visual-kit

One script for the SVG drawings in my CFA Level I study chats. Each drawing ends with one line:

```html
<script src="https://cdn.jsdelivr.net/gh/arielnudman0-hash/cfa-visual-kit@COMMIT/cfa.min.js"></script>
```

(`COMMIT` = the exact commit the skill pins, so a drawing never changes after it is made.)

What it does, in the browser, after the drawing streams in:

- **People kit**: if the drawing uses `<use href="#cast-...">` or `#prop-...` without defining them, it adds the full kit (head, torso, shoes, stand / hold / point / pull / push / sit poses, props, and the switchable faces, glasses, hats, suit, overalls, badge). Colours come from CSS variables on the person's `<g>` (`--sh`, `--pa`, `--sk`, `--ha`, ...).
- **Layout**: lays out `<g data-fx>` formula lines and `<g data-frac>` stacked fractions, wraps `data-wrap` captions, sizes `data-hug` bands and plates and `data-ring` rings around the words they mark, and shrinks or wraps text that would overrun its box or the drawing.
- **Repairs**: colours lost on shapes stamped with `<use>`, shapes painted black by an undefined colour, near-black panels behind words (light mode), words under 3:1 contrast in light or dark mode, a `</tspan>` / `</text>` mix-up that hides the rest of a drawing, and an empty title band.

No data is collected; the script only rearranges the drawing it runs in.
