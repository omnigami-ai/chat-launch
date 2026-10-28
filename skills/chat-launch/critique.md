# Critique

Be a harsh motion director who didn't build this. Default: reject. Look at the
pictures; don't score from the code.

## What to look at

- `node scripts/compare.mjs reference film out/compare-16x9.png --size 16:9`, and the same with `--size 1:1` and `--size 9:16`: the reference above yours at one moment in every state, in every shape.
- `node scripts/render.mjs film --size 9:16 --stress`: the quick test's sheets in `out/stress/`, with the words at their longest and shortest.
- Strips around the fast moments, in every shape (see SKILL.md step 6).
- `node scripts/render.mjs film --size 9:16 --phone`: one frame a second at 360 px wide.
- The MP4s themselves, at full size, twice: once for picture, once for sound.

Score each shape on its own; a film ships when every shape does.

## Score each 1–10

1. **Timing:** every state lands on the same beat as the reference; the drop is on beat 12.
2. **Camera:** one eased move per scene; no zoom in and out back to back; nothing important leaves the frame, in any shape.
3. **Continuity:** every scene is made from the one before (composer → phone, button → object, flood → bubble, button → page, dot → mark). No cut, no crossfade, no pop from one frame to the next.
4. **Fit:** every word fits its box with room to spare, in every state and every shape; nothing is clipped by a rounded corner, the phone's edge or the frame; nothing crowds its frame or is lost in it.
5. **Readability:** no text smaller than the table in `style.md`; the composer, the card titles, the outro and the lockup are readable on the `--phone` sheet.
6. **Truth:** every state shows something the product really does, in its words, with sample data; the two pills are real actions.
7. **Craft:** even spacing; one stroke weight; cards look like the product's objects, not placeholders; the mark is the product's own.

## Hunt for

- **Breathing room** (a failure here caps the film at 7): an action the viewer can't follow on one viewing: a click within half a second of the camera or cursor arriving, a result gone in under a second, a caption or headline replaced before it can be read. Lengthen the film rather than compress the holds.
- **Type centred in its container** (pills, buttons, chips, badges, a word beside a mark): the capitals sit on the container's centre line, measured, not by eye. Words that ride high are the usual fault (textBaseline 'middle' and CSS line boxes both centre the font's em box, not the letters); draw with `kit.centreText`, and in HTML use `text-box: trim-both cap alphabetic` with equal padding. The quick test fails canvas text set with 'middle'; captured screens and HTML are checked on the stills.
- **The film's own shapes, finished:** every click has a press state on its visual onset (what's pressed sinks a few percent and lights or darkens, then comes back), and a held control shows it's held; apertures and reveals are clean circles or the product's own shapes, never blades or drawn lines; a shape that becomes another does it in one continuous move, not a chain of in-between shapes; a pulse is one thin ring that thins as it grows; nothing (a check, a label, an icon) vanishes or appears in a single frame at a hand-off: it moves, shrinks or is covered. Check each on a strip of consecutive frames from the MP4.
- a flood that reads as a flash (under 0.18 s) or leaves a corner uncovered;
- the card or the pill drawn under the flood, or the flood drawn over the chat after it has shrunk;
- the bubble's words jumping when the flood hands them to the bubble;
- the cursor covering the label it's about to click;
- a state that holds with nothing moving for more than a second;
- a long request that wraps onto a fourth line, a reply that runs into the card, a pill that pushes the second pill off the phone;
- a glow still visible after the drop;
- a screen of the product drawn rather than captured; the cursor entering from inside the frame rather than from below it;
- words, logos or screens of another company;
- a click with no visible response on that beat.

For every mismatch write: state and time, what's wrong, and the exact fix
("flood lands 4 frames late: move T.drop from 5.48 to 5.45"). Fix the five
that matter most, compare again, score again. Nothing ships below 8.

With each fix, write what it must keep (the timing, sizes and moves
already right) and the times to look at again; look at them, and at the
cuts either side, before scoring again. If the same problem survives two
fixes, stop fixing it and report it with what you tried. Never loosen a
check, a size floor or the bar to get a pass. After three rounds, report
what remains instead of claiming it is finished.
