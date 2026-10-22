# Remake spec: @twoclipping's chat launch, now Ostlery

Reference: https://x.com/twoclipping/status/2104446706741825818, from his
guide "How I Make $10K Launch Videos for $0 with Opus 5.5" (local copy
`reference/motion/twoclipping-chat-launch.mp4`, not committed; his prompt is
`reference/motion/twoclipping-chat-launch-prompt.txt`). Made in code by Opus
5.5. Measured on stills every 0.5 s, every frame around the fast moments,
full-resolution crops of each state, and the audio's onsets.

## Format
1920 × 1080, 60 fps, 14.77 s (886 frames). One continuous take, no cuts.
130 BPM: a beat every 0.4615 s, 32 beats. Kicks measured at 5.47, 5.92,
6.39, 6.84 … 14.23 s (spacing 0.461 s; the detector reads about 0.03 s
early), so the drop is beat 12 (5.54 s on the grid); every visual event
below lands within 3 frames of a beat.
Canvas `#f5f5f2`; outro `#0d0c0f`. Geist for UI; a serif wordmark at the end.

**Now Ostlery, tall (2026-10-17).** The reference was first rebuilt in three
shapes for an earlier example product, its screens drawn in code (the "First
rebuild" column below). It is now Ostlery's, tall only, on the app's captured screens, with
whole beats added wherever a result needs a second to land (43 beats,
19.8 s; since 2026-10-21, 50 beats, 23.1 s, with reading time for its words); `style.md`'s states table maps
every beat. The measurements below are still the original's.

The original is wide only, and everything below is measured in wide. Our film
adds square (1440 × 1440) and tall (1080 × 1920), laid out from these numbers
for their own frames: the same beats, other camera framings and scales
(`style.md`, "Shapes").

## World and camera
Everything before the drop and in the chat lives on a phone screen of
428 × 900 world px (11 px bezel, screen radius 44). The camera is one
transform: [t, zoom, x, y] = the world point at the screen centre, eased,
zoom interpolated in log space. Measured from the composer's and the bezel's
on-screen widths:

| t (s) | zoom | world y at centre | what |
|---|---|---|---|
| 0.00 | 2.74 | 70 (composer centre) | composer, 1 line, 1094 × 147 on screen |
| 1.00 | 2.87 | 83 | slow push while typing |
| 2.50–2.80 | 3.05 | 95 | 3 lines, 1213 × 311 on screen |
| 3.10 | 2.80 | 165 | pull back as the phone forms |
| 3.60–4.00 | 2.50 | 372 | on the thinking object; bezel 395–1526 px |
| 5.00 | 2.66 | 372 | slow push during the tosses |
| 7.70–8.00 | 1.50 | 384 | chat; bezel 622–1298 px (screen 642 px) |
| 8.00 → 8.40 | 1.50 | 384 → 520 | pan down to the pills |
| 10.10 → 10.37 | 1.5 → ~3 | the button | push into the growing button |

x stays on the phone's centre (214) throughout.

## Beats

| t (s) | beat | event (original) | First rebuild |
|---|---|---|---|
| 0.10–2.50 | 0–5 | request types on 3 fixed lines; line 2 starts 1.08, line 3 1.85 | "Who's fed up with Vantora / and asking for something / simpler? Hot leads only" |
| 2.70–2.78 | 6 | send pressed | send (the product's green-black) |
| 2.80–3.00 | 6 | lime fill ripples out of the send button over the composer (0.2 s) | amber fill |
| 2.92–3.30 | 6–7 | composer's sides snap out to the screen, body grows down, bezel appears; send button becomes the orange wok | becomes the hot radar |
| 3.00 | 7 | "Finding something for you…" rises, shimmers | "Reading every mention…" |
| 3.69, 4.15, 4.62, 5.08 | 8–11 | wok tosses 6 coloured ingredients | radar dips and tosses 6 source blips |
| 5.48–5.68 | 12 | lime circle floods out of the wok, edge to edge (0.2 s) | amber flood from the radar |
| 5.70–5.95 | 12–13 | cards burst from the centre into a strip | 7 lead cards |
| 5.95–6.65 | 13–14 | strip slides three cards onto the chosen one | same |
| 6.92–7.10 | 15 | chosen card lifts (×1.13, 15 px up); "Best match" pill pops | same |
| 7.50–7.90 | 16–17 | side cards fly out; lime shrinks into the user's bubble carrying its words; card flies into its chat slot; phone appears | same |
| 7.86–8.00 | 17 | reply rises in | "Found it. **A hot lead** on r/SaaS…" |
| 8.23 | 18 | "Want me to order it for you?" rises | "Want an angle for your reply?" |
| 8.40, 8.48 | 18 | two pills pop (black, outline) | "Get the angle", "More leads" |
| 8.45–9.05 | 18–19 | cursor enters from bottom right, lands on the black pill | same |
| 9.20–9.30 | 20 | press (pill ×0.94); label slides up out | same |
| 9.38–9.74 | 20–21 | spinner | same |
| 9.80 | 21 | "✓ Ordered" rises, lime check | "✓ Angle ready", amber check |
| 10.10–10.37 | 22 | the button grows into the page, a pill until it passes the edges; label grows to 78 px | same |
| 10.50 | 22 | label rises out | same |
| 10.62–11.00 | 23–24 | line 1 rises word by word, 0.13 s apart | "Someone wants to switch." |
| 11.36 | 24 | line 1 rises out | |
| 11.45–12.00 | 25–26 | line 2 word by word | "Reply while the thread is active." |
| 11.62–12.05 | 25–26 | a dot rides a line (dotted ahead, lime behind) to a pin | amber signal dot |
| 12.05–12.30 | 26 | the pin becomes the brand mark (145 px) | the product's mark, amber |
| 12.46 | 27 | line 2 rises out | |
| 12.50–12.95 | 27–28 | mark spins once and moves into the lockup (115 px) | same |
| 12.95–13.25 | 28 | wordmark wipes out from behind the mark | the product's name |
| 13.30, 13.42 | 29 | line below rises; line above fades in | "Signal, not noise." / "Competitive intelligence" |
| 13.42–14.77 | 29–32 | hold | |

## Boxes (screen px at 1920 × 1080 unless marked world)

| Element | Measured |
|---|---|
| composer | world 400 wide; 53 tall at 1 line, +24.5 per line; radius = pill at 1 line, ~24 at 3; text padding 18 |
| send button | world 34 across, 4 from the right and bottom edges |
| wok / thinking object | world ~160 across, centre (214, 452) |
| user bubble (chat) | world x 21–407, y 44–137 |
| strip card | 330 × 440, radius 28; spacing 365; scale 1 − 0.025·d² by distance d from centre; the chosen card ×1.13 |
| "Best match" pill | 187 × 38, 26 px above the card |
| chat card | world 300 × 400 at x 29, y 224 (450 × 600 on screen); photo 60% of the height |
| pills | world 44 tall at y 686; gap 8 |
| outro line | centred, baseline 505 |
| route line | y 690, from 618 to 1310 |
| lockup | mark 115 tall; mark + wordmark 520 wide, centred; rows 437–552 |

## Type (px on screen at 1920 × 1080)

| Where | Original | Ours |
|---|---|---|
| composer | 47 → 50 (world 16.5) | same |
| thinking label | 38 (world 15), grey `#979699`, dark shimmer | same |
| user bubble | 22.5 (world 15) | 24.75 (world 16.5) |
| reply / question | 22 (world 14.5) | 25.5 (world 17) |
| card title / line / price | 35 / 18 / 24 (world 23 / 12 / 16) | 33 / 22 / 27 (world 22 / 14.5 / 18), plus the quote at 30 (world 20) |
| pill labels | 22.5 (world 15) | 24.75 (world 16.5) |
| "Best match" | 13 | 16 |
| done label at headline size | ~78 | 78 |
| outro lines | 92, weight 600, white | 92, cream `#efeadb` |
| lockup: above / wordmark / below | 22 grey / serif ~110 / serif 58 | 26 grey / Geist 600 112 / Geist 400 52 |

The original's chat text is small (22 px): unreadable at phone width. Ours is
10–20% larger everywhere in the chat and never smaller.

## Colour logic (original → ours)

| Role | Original | First rebuild |
|---|---|---|
| canvas | `#f5f5f2` | same |
| UI black | `#0e0e10` | `#0c1614` (the product's dark) |
| flood, user bubble, check | lime `#cdf24f` | amber `#e5a347` |
| thinking object | orange `#ff6a2a` | hot `#e56d47` |
| send button | blue `#2f6bff` | `#0c1614` |
| glow | conic pink, orange, lime, cyan, violet, blurred | pink, orange, amber, teal, blue, violet |
| cards | dark, food photo on top | dark, a tinted panel with the lead's quote on top |
| brand mark | Claude's, coral | the product's, amber |

## Motion
- Springs: card burst (260, 22), lift (260, 18), pills pop (320, 17), mark grows (200, 15), composer height (300, 22).
- Flood radius grows as p^1.25 over 0.2 s, from the object's size to past the far corner.
- Text rises out of a mask line (ease-out expo, 0.3 s) and leaves through the top (0.22 s).
- The button's growth is log-space (a zoom), ease-out, 0.29 s.
- Motion blur: 8 sub-frames across half a frame (`--blur 8`).
