---
name: chat-launch
description: Make a 20-second chat-style launch video for a product in code, one continuous take at 130 BPM, on the product's real screens - a request typed into its own composer with a glow around it, the send flooding the screen and landing as the message, the product working one step a beat, a colour flood on the drop that bursts into its own result cards, the best one flying back into the chat, a click on its real action, and an outro where the button grows into the page and ends on the brand mark. Renders a tall (9:16) MP4 with sound. Use when the user asks for a launch video, product video, promo, teaser or motion graphics for a product you ask for something - an assistant, search, booking, ordering.
---

# Chat launch

You make a 20-second launch film for the user's product in the style of the
viral "chat launch" videos: someone asks the product for something, it
works on it, the answer floods in as cards, the best one becomes the reply,
they click, and the button grows into the end card. One continuous take:
every scene is made from the one before it. You work by **adapting a
finished film**, not from a blank page: `reference/` is a complete film for
Ostlery (a fictional company made for omnigami's examples: an assistant that
finds small stays and books them), built against the original and measured
(`spec.md`). Its screens are Ostlery's real app, captured; the film's own
shapes (the glow, the floods, the button, the outro) stand on top of them.
Keep its motion; change its content.

The film is tall (1080 × 1920). The phone's screen is the world the camera
moves through, in the app's CSS px (390 wide); the phone around it is a
photograph of an unbranded phone (`assets/art/phone.png`).

Read `style.md` before you start and `critique.md` before you judge.

## Before you start

1. **Check the tools:** `node -v` (20 or later), `ffmpeg -version`, and a Chrome, Chromium, Edge or Brave install (`scripts/chrome.mjs` finds it; `CHROME_PATH` overrides). If something is missing, say how to install it and stop.
2. **Ask once, in one message,** for what the user hasn't given: the product's URL (and a demo account if its screens are behind a sign-in), the one request a user would type into it, and the two closing lines. If they want no questions, decide from the site.

## Steps

`SKILL_DIR` is the folder this file is in. Work in `chat-launch-film/` in the current directory.

1. **Set up.**
   ```bash
   mkdir -p chat-launch-film && cp -R "$SKILL_DIR/reference" chat-launch-film/reference && cp -R "$SKILL_DIR/reference" chat-launch-film/film && cp -R "$SKILL_DIR/scripts" chat-launch-film/scripts
   rm -rf chat-launch-film/reference/out chat-launch-film/film/out
   cd chat-launch-film && npm init -y >/dev/null && npm i -D puppeteer-core
   ```
   `reference/` stays untouched, for comparison. You edit `film/`.
2. **Learn the product.** `node scripts/capture.mjs <url> capture`, then look at every screenshot and read `capture/brand.json`: its name, words, colours, logo and what it actually does. Then use it on a phone-sized window: ask it the request and follow what it really does, step by step.
3. **Map the story onto the product.** Never refuse a product and never force one into the reference's content: keep the film's moves and change what each one carries.
   - **Find the thing that travels:** the request, from the moment it's typed to the result the user acts on (Ostlery: the trip, then the stay it books).
   - **Write the story in one sentence, from the product's real flow,** and check it: every scene is a step the product really takes, in its order, once, and the end is the real result.
   - **Swap a beat when the product doesn't have it; don't invent a feature for it.** Each beat has stand-ins:

     | Beat | Reference (Ostlery) | Stand-ins |
     |---|---|---|
     | the ask | the request typed into the app's own composer | a search box, a prompt, a form's main field |
     | thinking, one step a beat (beats 8–11) | the search's four checks, each with its count | the product's own progress: steps, sources read, a count, a status line; or one working state held over the beats |
     | the burst | the six stays, captured one by one | the product's result objects: rows, cards, files, matches |
     | the best | the best fit flies back into its slot in the chat | the result the product puts first |
     | the action | "Book it" → "Booking" → "Booked" | the product's real next step and its real states |
     | the close | two lines, the mark, the wordmark | same, in the product's words |

   - **Say what changed.** Write the sentence and the state list to `film/STATES.md` (a table: time, state, what it shows, words on screen), and tell the user in a line which beats you swapped and why.
4. **Capture the product's real screens.** Write `film/plans/mobile.json` in the shape of `reference/plans/mobile.json` (the format is at the top of `scripts/screens.mjs`), at 390 × 844, scale 4: the start page (`home`); the composer after every keystroke of the request (`ask-01` … `ask-NN`, a `type` step capturing `around` the composer); the working states, one per beat (`think-0` … `think-4`; the reference reaches each with an `eval` that shows that many checks done, the states the app passes through); the answer (`results`); each result card on its own (`stay-0` … `stay-5`, scrolling the row to each); and the action's states (`booking`, `booked`, at the answer's scroll). Record `rects` for the composer and its send button, the message bubble, the working card and its spinner, the last count, the result cards, the reply lines, the actions and the button. Clear the composer before leaving the start page, as the app does on send. Then:
   ```bash
   node scripts/screens.mjs film/plans/mobile.json film/assets/screens
   (printf 'window.SCREENS = '; cat film/assets/screens/screens.json; printf ';\n') > film/assets/screens/screens.js
   ```
   The film reads its captures and rects from `screens.js` (a sandboxed preview can't fetch the JSON). Never draw a screen of the product for the film: what the viewer reads as the product is a capture of it.
5. **Adapt `film/index.html`.** It is one file with labelled sections:
   - `DEFAULTS` and `FIELDS`: the two outro lines and the tagline. `KICKER`, `WORDMARK`, `DONE`: the end card's small line, the name, and the done label the button grows with.
   - colour and type: `PAPER`, `INK`, `EMBER` (the accent: the floods, the dot, the mark), `OK` (the done state's colour, if the product has one), and the product's two faces (Ostlery: Figtree and Newsreader, SIL Open Font License, in `assets/fonts/`). `MARK`: the product's mark as `Path2D`s from its SVG.
   - `SCREEN`, `BAR`, `PHONE_SCREEN`: the phone and its status bar; keep them.
   - `askScreen`, `thinkScreen`, `chatScreen`, `bookPill`: each scene's screen, built from the captures and their rects. `thinkScreen` grows the working card a row at each toss and spins its spinner; `chatScreen` lets the reply rise line by line and the actions pop in; `bookPill` takes the button through its states (its label leaves, the next rises; the done colour fills out from the check).
   - `stripCards`, `drawStay`: the result cards (from `stay-N`), their burst, slide and lift; `CARD_W`, `CARD_H` from the card captures.
   - `camKeys`: where the camera looks in each scene and how close, in the world's CSS px: the composer, the working card, the chat before and after the pan, the push into the button.
   Keep the motion code as it is: `T` (the beats), `SEND`, the camera's times, the springs, the floods, the burst and slide, the fill, the cursor's times, every `press`.
   Keep every text size of the film's own words (the table under "Type" in `style.md`). If words don't fit, cut words; never shrink the type below it.
6. **Check stills against the reference.**
   ```bash
   node scripts/compare.mjs reference film out/compare-9x16.png --size 9:16
   ```
   It renders both films at one moment inside every state, the reference above yours. Look at it properly. Then run the quick test and the phone check:
   ```bash
   node scripts/render.mjs film --size 9:16 --stress
   node scripts/render.mjs film --size 9:16 --phone
   ```
   The quick test fails if a word leaves the frame, overlaps another or falls under the size floor, with the words at their longest and at their shortest; its notes about crops the camera makes on purpose (the status bar's clock while it's close on the screen) are not failures. Look at every sheet it writes to `out/stress/` for what it can't measure: a word clipped by a card or a rounded corner, a frame that looks crowded or empty. Fix anything that fails `critique.md`, then compare again. Repeat until every score is 8 or more.
7. **Check the motion** on strips of consecutive frames from the MP4 (step 9), around every hand-off: the send (3.6–4.4), each toss (4.62, 5.08, 5.54, 6.0), the drop (7.3), the burst and slide (7.5–8.6), the card flying home (9.8–10.3), the click and its states (12.4–13.4), the fill (14.2–14.6) and the mark (16.4–18.0). Then check the breathing room at every beat (`style.md`): nothing acted on the instant it appears, every result held a second. Then **get a fresh judgement**: if your agent can start a sub-agent without this session's memory, give it `critique.md` and the images, nothing else, and fix the worst problems it finds; otherwise reread `critique.md` and score from the images alone, as a stranger would.
8. **Check it's repeatable:** `node scripts/render.mjs film --size 9:16 --check` must pass.
9. **Render.**
   ```bash
   node scripts/render.mjs film --size 9:16 --video --blur 4 --music --sound --poster 8.4
   ```
   This writes `out/9x16.mp4` (1080 × 1920): 60 fps, motion blur, a synthesised 130 BPM bed and effects from omnigami's own sound kit, loudness about −14 LUFS, and a poster (`out/9x16-poster.png`). For the user's own song, use `--audio song.wav` instead of `--music`; it's fitted to the film by `song.mjs`: it starts on a bar line and, near the end, lands one hit and closes and fades (cleanest with the song's stems in a `song-stems/` folder beside it: the drums stop on that hit). A song near 130 BPM fits the film's cuts; `--from <seconds>` starts at another section of it, such as 16 beats before its drop. Run it in the foreground and wait for the file.
10. **Write `chat-launch-film/README.md`:** what each file is, where to change a word, how to recapture the screens, and the render command. Also write `out/CAPTION.md`: a post to share the film on X or LinkedIn, under 280 characters, in the product's own words, with its URL; no hashtags unless the user asks.
11. **Report:** the MP4, the poster, the caption, the story sentence and state list, which beats you swapped, the final scores, and the one change that would improve it most.

## Rules

- **Only what the product does.** Every state is a capture of the product doing it, in its own words; the action is real; sample data only, no real customer data or real company names.
- **A story that holds.** One thing travels the whole film; every step is real, in the product's order, once; the end is the real result.
- **Let each result land.** Keep the reference's holds, and lengthen by whole beats rather than cut one: the request holds a second before it sends, the last step of the work a second before the drop, the best result a second before it flies, the reply is read before the actions, the cursor rests before its click, the done state holds a second, each closing line is read before the next.
- **Keep the motion.** Timing, camera, springs and floods come from the reference. If content doesn't fit, shorten the words before changing a box.
- **Every click has a press state**, and shapes change in one move (`style.md`, Motion).
- **Keep the engine rules** (`style.md`): `seek(t)` paints from its arguments only; no clocks, no `Math.random`, no timers, no network; every file inside `film/`.
- **Only the user's brand.** No other company's name, logo or UI: the phone is the reference's unbranded photograph, its status bar generic.

## Files

- `reference/`: the Ostlery film (`index.html`), its capture plan (`plans/mobile.json`) and captures (`assets/screens/`, with `screens.js`), the unbranded phone (`assets/art/phone.png`), fonts (Figtree and Newsreader, SIL Open Font License), `kit.js` (springs, text fitting). Ostlery is a fictional company made for omnigami's examples.
- `scripts/`: `capture.mjs` (brand from a URL), `screens.mjs` (the product's real screens, from a plan), `render.mjs` (stills, strips, the quick test, checks, MP4s), `compare.mjs` (reference against yours), `preview.mjs` (a local preview that edits the words), `music.mjs` (the bed), `song.mjs` (fits a supplied song) and `sfx.mjs` (effects from the kit in `sounds/`), `chrome.mjs`.
- `style.md`: the grammar, the states, the motion numbers, the banned list.
- `critique.md`: how to score and what to hunt for.
- `spec.md`: the measurements of the original the reference was built from.

Style inspired by [@twoclipping's video](https://x.com/twoclipping/status/2104446706741825818). This skill is an independent style study; he did not make or endorse it.

This skill is omnigami's (https://omnigami.ai), © 2026 Auberon LLC. Use what it makes for anything,
commercial work included, and change the skill for your own use; don't redistribute or
sell the skill. Full terms: https://github.com/omnigami-ai/skills/blob/main/LICENSE.md
