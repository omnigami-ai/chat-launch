# Chat launch: style

One continuous chat-to-action film, built on captured product screens.
The layout and motion measurements are in `spec.md`.

## The grammar

- **One continuous take, on the product's real screens.** Every scene is made out of the one before it: the send floods the screen and lands as the message, the working card grows a row a beat, a colour floods out of its last count, the results burst out of the flood, the flood gathers in behind the best one as it flies home, the button grows into the page. The screens are captures; the film's own shapes (the glow, the floods, the button, the outro) stand on top of them and hand off to them.
- **The camera makes one move per scene** on eased keyframes, and never zooms in and out back to back: a slow push while typing, a pull back and push onto the working card as the message lands, a slow push while it works, a pan down the chat, a push into the button.
- **Something happens on every beat, and every result lands:** 130 BPM, a beat every 0.4615 s, 50 beats, 23.1 s. The drop is beat 18. Add whole beats where the viewer has something to read or find: a completed request needs reading time before it sends, and a result needs time to be found. Pause after a response arrives, never on the product's own working (the founder, 2026-10-21: words to read get about a quarter second a word; a big move gets room before the press that follows it; the checks, the counts and the cards bursting are the product working and keep their pace; a hold is simply still, never a slow push that stops):
  - the typed request holds 2.1 s before it sends (16 words, most read as they type);
  - the checks run straight on, and "Checked 312 lake cabins · 6 fit" goes into the drop without an extra pause;
  - the lifted best holds a second before it flies;
  - the reply arrives with its two actions, as one response (the buttons follow the question by a third of a second), then holds still to be read: the cursor sets off about 1.4 s after the buttons settle and hovers 0.45 s on "Book it" before it clicks, a natural hover then click (reply to click, 3.2 s);
  - the done state holds a second;
  - each closing line is read before the next: line 1 (8 words) for 1.85 s, line 2 (4 words) for 1.3 s.
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
| 4.61 | 10 | send | the send button is pressed; the accent floods the screen from it (0.22 s) and lands as the message (to 5.23); its words rise in |
| 5.54–6.92 | 12–15 | four tosses | the product does one thing per beat (Ostlery: a check ticks and its count shows; the card grows a row, its spinner riding the card's growing edge); the last result holds |
| 8.25 | 18 | drop | the accent floods out of the last count, edge to edge in 0.2 s |
| 8.47 | 18 | results | the product's own result cards burst from the centre |
| 8.72 | 19 | slide | the column slides three cards onto the best one |
| 9.69 | 21 | best | it lifts, and holds |
| 10.82 | 23 | chat | the flood gathers in behind the best card as it flies into its slot in the chat; the others fly off |
| 11.09 | 24 | reply | the reply rises line by line, then the question (11.46), then the product's two real next steps (11.81): one response; it holds still to be read |
| 14.31 | 31 | click | the cursor (in at 13.46) has hovered 0.45 s; press; the label leaves, the working state rises with its spinner; the done state (14.86) fills out from its check and holds |
| 16.08 | 35 | fill | the button grows into the page, its done label to headline size |
| 16.62 | 36 | line 1 | what the user wanted, in a few words |
| 18.69 | 40 | line 2 | what the product did; a dot rides a line to the end |
| 19.73 | 43 | mark | the dot waits at the end as the line leaves, sets off upward (20.12) and only then becomes the mark, crossfading in the first tenth of its move so the swap hides in the motion; it grows into the mark as it glides to the centre; the wordmark rises under it, then the tagline and the kicker; the end card holds to 23.1 |

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
- **The mark** waits as the dot while the line leaves, then grows (log space) and glides upright to the centre of the end card in one move: fast out, soft landing. The dot becomes the mark only once it's moving (a 4-frame crossfade at the same size and centre, early in the rise), never on the stopped dot, where the swap would show. The end card is stacked (kicker, mark, wordmark, tagline), so the mark never reads as a letter beside the name.
- **Motion blur:** 4 sub-frames (`--blur 4`).

## Sound

A `tick` per keystroke, a `tap` on the send and the click, `swish`es on the
floods, the burst, the slide, the chat, the fill and the mark's move (each with
its `motion`), a `pop` per toss and on each arrival. No impacts or risers. The
effects come from omnigami's own kit; `scripts/sounds/kit.json` says what each
one is for. The soundtrack is the skill's own song (`music/song.mp3`, bubbly, bright
synth-pop at 130 BPM), landing one hit on the first outro line (`--land 16.62`) as its
drums stop and the rest fades. With `--music`, the synthesised 130 BPM score instead: pads
and hats for 18 beats, then the drop. Mastered around −14 LUFS.

The score's sound is `music.style`: here `'synth'`, the default. For the user's product, pick by what it is: `'organic'` for plants, food and drink, and other natural or handmade things; `'synth'` (oscillators, the default) for software and tools; `'felt'` (a sparse felt piano over a sub bass and a light kit) for a quiet, minimal film. In a break (`music.breaks`) the drums, bass and lead stop and the chords play on; the film's name seeds the key (always major), the progressions and the patterns.

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
