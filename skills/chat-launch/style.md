# Chat launch: style

Style inspired by [@twoclipping's video](https://x.com/twoclipping/status/2104446706741825818),
made in code with Claude Opus 5.5 from a prompt he published openly. The
reference film here is our own, built and measured against it (`spec.md`).

## The grammar

- **One continuous take, on the product's real screens.** Every scene is made out of the one before it: the send floods the screen and lands as the message, the working card grows a row a beat, a colour floods out of its last count, the results burst out of the flood, the flood gathers in behind the best one as it flies home, the button grows into the page. The screens are captures; the film's own shapes (the glow, the floods, the button, the outro) stand on top of them and hand off to them.
- **The camera makes one move per scene** on eased keyframes, and never zooms in and out back to back: a slow push while typing, a pull back and push onto the working card as the message lands, a slow push while it works, a pan down the chat, a push into the button.
- **Something happens on every beat, and every result lands:** 130 BPM, a beat every 0.4615 s, 43 beats, 19.8 s. The drop is beat 16. The original's beats were too tight to read (a request sent the instant it's typed, a result gone in a third of a second), so ours add whole beats: the full request holds a second before it sends, the last count a second before the drop, the lifted best a second before it flies, the reply is read before the actions arrive, the cursor rests half a second before its click, the done state holds a second, and each closing line is read before the next.
- **The product's own colours:** its paper behind the phone, its ink for the outro, one accent for the floods, the dot and the mark (Ostlery: ember `#C2482B`), and the product's done colour where it has one (Ostlery's green "Booked"). A soft rotating glow around the composer while it's typed, and around the phone while it works; none after the drop.
- **Text rises out of a mask line** and leaves through the top. The outro lines rise word by word.
- **Every click has a press state**; shapes change in one move (see Motion).

## The frame

Tall, 1080 × 1920. The world is the phone's screen in the app's CSS px (390
wide, the status bar 44 px above the page); the phone around it is a
photograph of an unbranded phone, scaled with the screen. The camera:

| scene | zoom | looks at (world y) |
|---|---|---|
| typing | 2.75 → 2.9 | the composer (444) |
| working | 2.85 → 2.98 | the working card (262) |
| chat, before → after the pan | 2.45 → 2.6 | 470 → 548: the cards, the reply and the actions |
| push into the button | 4.8 | the button |

The result cards stack in a column 640 px apart, 470 px wide; the best one
lifts by 10 % and its neighbours fly off the top and bottom. The flood's final
radius is 1.23 × the distance to the far corner.

## The states (t = when it starts)

| t (s) | beat | State | What it becomes for another product |
|---|---|---|---|
| 0.00 | 0 | ask | the one request, typed into the product's composer (a capture per keystroke, done by 2.5 s), a glow around it; it holds |
| 3.69 | 8 | send | the send button is pressed; the accent floods the screen from it (0.22 s) and lands as the message (to 4.31); its words rise in |
| 4.62–6.00 | 10–13 | four tosses | the product does one thing per beat (Ostlery: a check ticks and its count shows; the card grows a row); the last result holds |
| 7.32 | 16 | drop | the accent floods out of the last count, edge to edge in 0.2 s |
| 7.54 | 16 | results | the product's own result cards burst from the centre |
| 7.79 | 17 | slide | the column slides three cards onto the best one |
| 8.77 | 19 | best | it lifts, and holds |
| 9.89 | 21 | chat | the flood gathers in behind the best card as it flies into its slot in the chat; the others fly off |
| 10.16 | 22 | reply | the reply rises line by line, then the question |
| 11.54 | 25 | two actions | the product's two real next steps pop in |
| 12.46 | 27 | click | the cursor has rested 0.5 s; press; the label leaves, the working state rises with its spinner; the done state (13.01) fills out from its check and holds |
| 14.24 | 31 | fill | the button grows into the page, its done label to headline size |
| 14.77 | 32 | line 1 | what the user wanted, in a few words |
| 15.78 | 34 | line 2 | what the product did; a dot rides a line to the end |
| 16.50 | 36 | mark | the dot waits as the line leaves, then grows into the mark as it glides to the centre; the wordmark rises under it, then the tagline and the kicker; the end card holds to 19.8 |

## The result cards

Each card is a capture of the product's own result object (a stay, a lead, a
track, a doc), one per capture, clipped to its corner radius. Use the
product's first result as the best one. Sample data only.

## Type

The film's own words are in the product's faces (Ostlery: Newsreader for the
outro lines and wordmark, Figtree for the done label, tagline and kicker).
Everything else is the product's, captured. Sizes in px at 1080 × 1920:

| Where | Size | Weight |
|---|---|---|
| done label at headline size | 78 | 600 |
| outro lines | 104, down to 62 for long lines (two lines at most) | 500 |
| end card, stacked: kicker / mark / wordmark / tagline | 32 / 230 tall / 170 / 56 | 500 / – / 600 / 400 |

Captured text keeps the product's size; the camera's zooms (2.45–2.98) keep
its body text at 30 px or more.

## Motion

- **Camera keys** (world point at the frame centre, zoom in log space): see "The frame". Eased: soft while typing, smooth into the pull-back, linear while working, in-out for the pan, smooth into the push.
- **Springs:** burst (380, 26; each card 210, 21), lift (260, 18), pills (320, 17), the working card's new row (300, 26).
- **Presses:** a pressed thing sinks to 0.95 over the 0.07 s before the click and comes back over 0.22 s; the cursor shrinks to 0.86.
- **Floods:** the send's radius grows as p^1.3 over 0.22 s, then the flood contracts in one move into the message (0.36 s); the drop's grows as p^1.25 over 0.2 s to past the far corner; after the burst it gathers into the best card's outline behind it.
- **The button's growth** is a zoom: log-space, ease-out, 0.29 s; its colour turns from the done colour to the outro's ink as it grows.
- **The mark** waits as the dot while the line leaves, then grows (log space) and glides upright to the centre of the end card in one move: fast out, soft landing. The end card is stacked (kicker, mark, wordmark, tagline), so the mark never reads as a letter beside the name.
- **Motion blur:** 4 sub-frames (`--blur 4`).

## Sound

A `tick` per keystroke, a `tap` on the send and the click, `swish`es on the
floods, the burst, the slide, the chat, the fill and the mark's move (each with
its `motion`), a `pop` per toss and on each arrival. No impacts or risers. The
effects come from omnigami's own kit; `scripts/sounds/kit.json` says what each
one is for. A 130 BPM bed: pads and hats for 12 beats, then the drop. Mastered
around −14 LUFS.

## Banned

Cuts; crossfades; blur-ins; 3D; particles; a camera that zooms in and out
back to back; glows after the drop; drawing the product's screens; words added
to the screens; invented features; another company's name, logo or UI; a
maker's phone or OS chrome (an island or notch, a home indicator, named OS
features): the phone is the unbranded photograph, the status bar generic.

## Engine rules

- `seek(t, values)` paints from its arguments only: no `Date`, `performance.now()`, unseeded `Math.random`, timers or network.
- A CPU-backed canvas (`getContext('2d', { willReadFrequently: true })`), and helper canvases (the glow) created the same way.
- `ctx.reset()` at the start of every frame, so no canvas state carries over.
- Every file the film loads is inside its folder; fonts load in `prepare()`.
