# Chat launch: layout and motion spec

A continuous chat-to-action film on a 130 BPM grid. The compact wide layout
below specifies the camera, boxes and motion; `style.md` gives the shipped
Ostlery film's tall layout and its longer reading holds. Use the product's
own words, working states, result objects, colours and mark.

Review stills every 0.5 s, every frame around fast moments, full-resolution
crops of each state, and the audio's onsets.

## Format

Compact wide layout: 1920 × 1080, 60 fps, 14.77 s (886 frames). One continuous
take, no cuts. At 130 BPM, a beat is 0.4615 s: 32 beats. Kick onsets at 5.47,
5.92, 6.39, 6.84 … 14.23 s are spaced 0.461 s apart; an onset detector can
read about 0.03 s early. The drop is beat 12 (5.54 s on the grid); visual
events land within 3 frames of a beat. The light canvas is `#f5f5f2`, the
outro `#0d0c0f`. Pair a UI sans such as Geist with a serif wordmark, or use
the product's own licensed faces.

The shipped Ostlery film is tall only, 1080 × 1920, on the app's captured
screens. Its base grid is 43 beats, 19.8 s; added reading holds make it
50 beats, 23.1 s. `style.md`'s states table maps those beats. The compact
numbers below are a layout option, not the shipped film's timeline.
For a square adaptation, use 1440 × 1440; for tall, use 1080 × 1920. Lay
out each frame with its own camera framing and scale.

## World and camera

For the compact wide layout, everything before the drop and in the chat
lives on a phone screen of 428 × 900 world px (11 px bezel, screen radius
44). The camera is one transform: [t, zoom, x, y] = the world point at the
screen centre, eased, with zoom interpolated in log space. Composer and
bezel widths set the framing:

| t (s) | zoom | world y at centre | what |
|---|---|---|---|
| 0.00 | 2.74 | 70 (composer centre) | composer, 1 line, 1094 × 147 on screen |
| 1.00 | 2.87 | 83 | slow push while typing |
| 2.50–2.80 | 3.05 | 95 | 3 lines, 1213 × 311 on screen |
| 3.10 | 2.80 | 165 | pull back as the phone forms |
| 3.60–4.00 | 2.50 | 372 | on the working object; bezel 395–1526 px |
| 5.00 | 2.66 | 372 | slow push during the working steps |
| 7.70–8.00 | 1.50 | 384 | chat; bezel 622–1298 px (screen 642 px) |
| 8.00 → 8.40 | 1.50 | 384 → 520 | pan down to the pills |
| 10.10 → 10.37 | 1.5 → ~3 | the button | push into the growing button |

x stays on the phone's centre (214) throughout.

## Compact beat grid

| t (s) | beat | event |
|---|---|---|
| 0.10–2.50 | 0–5 | request types on 3 fixed lines; line 2 starts 1.08, line 3 1.85 |
| 2.70–2.78 | 6 | send pressed |
| 2.80–3.00 | 6 | accent fill ripples out of the send button over the composer (0.2 s) |
| 2.92–3.30 | 6–7 | composer's sides snap out to the screen, body grows down, bezel appears; send button hands off to the product's working object |
| 3.00 | 7 | working label rises and shimmers |
| 3.69, 4.15, 4.62, 5.08 | 8–11 | working object performs a step per beat; up to 6 progress items |
| 5.48–5.68 | 12 | accent circle floods from the working object, edge to edge (0.2 s) |
| 5.70–5.95 | 12–13 | result cards burst from the centre into a strip; up to 7 cards |
| 5.95–6.65 | 13–14 | strip slides three cards onto the chosen one |
| 6.92–7.10 | 15 | chosen card lifts (×1.13, 15 px up); best-result pill pops |
| 7.50–7.90 | 16–17 | side cards fly out; accent shrinks into the user's bubble carrying its words; card flies into its chat slot; phone appears |
| 7.86–8.00 | 17 | reply rises in |
| 8.23 | 18 | follow-up question rises |
| 8.40, 8.48 | 18 | two action pills pop (ink, outline) |
| 8.45–9.05 | 18–19 | cursor enters from bottom right and lands on the primary pill |
| 9.20–9.30 | 20 | press (pill ×0.94); label slides up out |
| 9.38–9.74 | 20–21 | spinner |
| 9.80 | 21 | done label rises with an accent check |
| 10.10–10.37 | 22 | button grows into the page, a pill until it passes the edges; label grows to 78 px |
| 10.50 | 22 | label rises out |
| 10.62–11.00 | 23–24 | line 1 rises word by word, 0.13 s apart |
| 11.36 | 24 | line 1 rises out |
| 11.45–12.00 | 25–26 | line 2 rises word by word |
| 11.62–12.05 | 25–26 | a dot rides a line (dotted ahead, accent behind) to its endpoint |
| 12.05–12.30 | 26 | endpoint becomes the product's brand mark (145 px) |
| 12.46 | 27 | line 2 rises out |
| 12.50–12.95 | 27–28 | mark spins once and moves into the lockup (115 px) |
| 12.95–13.25 | 28 | wordmark wipes out from behind the mark |
| 13.30, 13.42 | 29 | tagline below rises; category above fades in |
| 13.42–14.77 | 29–32 | hold |

## Boxes (screen px at 1920 × 1080 unless marked world)

| Element | Dimensions |
|---|---|
| composer | world 400 wide; 53 tall at 1 line, +24.5 per line; radius = pill at 1 line, ~24 at 3; text padding 18 |
| send button | world 34 across, 4 from the right and bottom edges |
| working object | world ~160 across, centre (214, 452) |
| user bubble (chat) | world x 21–407, y 44–137 |
| strip card | 330 × 440, radius 28; spacing 365; scale 1 − 0.025·d² by distance d from centre; the chosen card ×1.13 |
| best-result pill | 187 × 38, 26 px above the card |
| chat card | world 300 × 400 at x 29, y 224 (450 × 600 on screen); product image or result media 60% of the height |
| pills | world 44 tall at y 686; gap 8 |
| outro line | centred, baseline 505 |
| route line | y 690, from 618 to 1310 |
| lockup | mark 115 tall; mark + wordmark 520 wide, centred; rows 437–552 |

## Type (px on screen at 1920 × 1080)

These are compact and enlarged layout settings. Use the enlarged chat
settings for readability; increase further when the phone-width check needs
it. The shipped tall film's captured body text stays at 30 px or more
through its camera zooms; see `style.md`.

| Where | Compact | Enlarged |
|---|---|---|
| composer | 47 → 50 (world 16.5) | same |
| working label | 38 (world 15), grey `#979699`, dark shimmer | same |
| user bubble | 22.5 (world 15) | 24.75 (world 16.5) |
| reply / question | 22 (world 14.5) | 25.5 (world 17) |
| card title / line / price | 35 / 18 / 24 (world 23 / 12 / 16) | 33 / 22 / 27 (world 22 / 14.5 / 18), plus a quote at 30 (world 20) |
| pill labels | 22.5 (world 15) | 24.75 (world 16.5) |
| best-result label | 13 | 16 |
| done label at headline size | ~78 | 78 |
| outro lines | 92, weight 600, white | 92, cream `#efeadb` |
| lockup: above / wordmark / below | 22 grey / serif ~110 / serif 58 | 26 grey / UI sans 600 112 / UI sans 400 52 |

Compact chat text at 22 px is unreadable at phone width. Make it 10–20%
larger throughout the chat, never smaller, and check it at 360 px wide.

## Colour logic

Use the product's own palette. These light and warm palette settings show
how the same roles translate between brands; Ostlery's current palette is
in `style.md`.

| Role | Light palette | Warm palette |
|---|---|---|
| canvas | `#f5f5f2` | same |
| UI ink | `#0e0e10` | `#0c1614` |
| flood, user bubble, check | lime `#cdf24f` | amber `#e5a347` |
| working object | orange `#ff6a2a` | hot `#e56d47` |
| send button | blue `#2f6bff` | `#0c1614` |
| glow | conic pink, orange, lime, cyan, violet, blurred | pink, orange, amber, teal, blue, violet |
| cards | dark, result media on top | dark, a tinted panel with a result quote on top |
| brand mark | the product's mark in coral | the product's mark in amber |

## Motion

- Springs: card burst (260, 22), lift (260, 18), pills pop (320, 17), mark grows (200, 15), composer height (300, 22).
- Flood radius grows as p^1.25 over 0.2 s, from the object's size to past the far corner.
- Text rises out of a mask line (ease-out expo, 0.3 s) and leaves through the top (0.22 s).
- The button's growth is log-space (a zoom), ease-out, 0.29 s.
- Motion blur: 8 sub-frames across half a frame (`--blur 8`).
