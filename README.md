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
- **Notation**: a division written in words between two numbers (`600 over 200`, `90 ÷ 360`) becomes a stacked fraction, making room above and below when there is none; a whole-number power written in words after a number or bracket (`1.06 to the 5th`, `(1 + r) squared`) becomes a superscript.
- **Reading**: a one-line text that would have to shrink under 10.5 px wraps at its own size instead, with room made under it; a ring around a word inside a sentence becomes a tight pill with space either side, so it never cuts the next word; short forms (NPV, WACC, YTM) whose words never appear on a drawing get a "Short forms" key line under it.
- **Spacing**: two separate words that run into each other move apart: on one line sideways (a 6 px gap), in a table cell the left label wraps onto two lines centred on its row, otherwise the smaller one-line text steps a few px to the nearest free spot; never off its box, onto a picture, or apart from its row pieces.

It runs once when the page's fonts are already loaded (again after they load otherwise), and measures each word once, so a chat with dozens of drawings stays responsive.

No data is collected; the script only rearranges the drawing it runs in.
