# cfa-visual-kit

One script for the SVG drawings in my CFA Level I study chats. Each drawing ends with one line:

```html
<script src="https://cdn.jsdelivr.net/gh/arielnudman0-hash/cfa-visual-kit@COMMIT/cfa.min.js"></script>
```

(`COMMIT` = the exact commit the skill pins, so a drawing never changes after it is made.)

What it does, in the browser, after the drawing streams in:

- **People kit**: if the drawing uses `<use href="#cast-...">` or `#prop-...` without defining them, it adds the full kit (head, torso, shoes, stand / hold / point / pull / push / sit poses, props, and the switchable faces, glasses, hats, suit, overalls, badge). Colours come from CSS variables on the person's `<g>` (`--sh`, `--pa`, `--sk`, `--ha`, ...).
- **Scene kit**: 59 realistic scene parts in the people kit's style (buildings: bank, house, shop, factory, bakery, tower, town hall; machines: press, conveyor, valve, gauge, lever; containers: tank, barrel, crate, box, sack, jar; money: coins, bills, money bag, padlock; a balance scale, fulcrum and plank; a clock; kitchen things; truck, ship, tree, sign, flag, balloons). A drawing places one with a single line, `<g transform="translate(x y) scale(s)"><use href="#scene-NAME"/></g>`, and the script adds only the parts that drawing uses (with any part they use). Parts stand on a ground line at the people's scale, light from the upper left, tinted by `--c` / `--c2`.
- **Layout**: lays out `<g data-fx>` formula lines and `<g data-frac>` stacked fractions, wraps `data-wrap` captions, sizes `data-hug` bands and plates and `data-ring` rings around the words they mark, and shrinks or wraps text that would overrun its box or the drawing.
- **A whole and its parts** (since v8): `<g data-split="TOTAL REVENUE $144">` holding one `<rect data-part="explicit costs $102">` per part gets ONE frame around the whole with the whole's name and amount just above its top-left corner, and each part's name and amount written INSIDE its own part (two short lines, the amount bold, dark or white ink by the part's colour; the words start at the drawing's own text size and never go under 10.5 px); a part too thin for its words gets its label just under the frame on a 2 px tick. A part drawn shorter than its true length carries data-break: the kit draws the axis-break zigzag (in the page colour) near its left end and keeps the words clear of it. The amount is the label's last number: $, €, %, m, bn, k, ¢, bp, days, years, trays, pies, a leading + or −, or a × factor.
- **Repairs**: colours lost on shapes stamped with `<use>`, shapes painted black by an undefined colour, near-black panels behind words (light mode), words under 3:1 contrast in light or dark mode, a `</tspan>` / `</text>` mix-up that hides the rest of a drawing, and an empty title band.
- **Notation**: a division written in words between two numbers (`600 over 200`, `90 ÷ 360`) becomes a stacked fraction, making room above and below when there is none; a whole-number power written in words after a number or bracket (`1.06 to the 5th`, `(1 + r) squared`) becomes a superscript.
- **Reading**: a one-line text that would have to shrink under 10.5 px wraps at its own size instead, with room made under it; a ring around a word inside a sentence becomes a tight pill with space either side, so it never cuts the next word. (Since v8 there is no "Short forms" key line: each drawing writes a short form's words itself, inside its label.)
- **Spacing**: two separate words that run into each other move apart: on one line sideways (a 6 px gap), in a table cell the left label wraps onto two lines centred on its row, otherwise the smaller one-line text steps a few px to the nearest free spot; never off its box, onto a picture, or apart from its row pieces.

- **Room**: a long line or a `data-wrap` block that needs more lines opens room right under its first line: everything below moves down across the drawing, or, when a picture blocks that, its own box grows (rows of equal boxes grow together) and the drawing makes room under the box. Shrunk lines are measured again, so nothing ends past the edge (the font widens as it shrinks).
- **Placement**: rings and hug bands sit exactly on their words even after things move; a template drawn at the top-left corner and stamped elsewhere with `<use>` moves into `<defs>`; a name plate over a person's head moves up off the head (else beside it); words painted under a later shape (a bar, a person, a rope, a box) come to the top with their tight plate; words crossing a picture or a shape of their own colour get a thin outline in the page colour.

It runs ONCE, after the fonts the drawing uses have loaded (2 s safety timeout), so the same drawing always lays out the same way, and it measures each word once, so a chat with dozens of drawings stays responsive.

No data is collected; the script only rearranges the drawing it runs in.
