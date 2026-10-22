# Chat launch · omnigami

Someone asks your product for something, and it delivers.

A 23-second launch film for products you ask for something, on your real screens. A request types into your own composer, your product works on it one step a beat, a colour floods the screen on the drop, its results burst in as cards, the best one flies back into the chat, and one click later it’s done, ending on your mark. One continuous take.

Watch it play live, and change its words, at [omnigami.ai/skills/chat-launch](https://omnigami.ai/skills/chat-launch).

## Install

In Claude Code:

```
/plugin marketplace add omnigami-ai/skills
/plugin install omnigami-chat-launch@omnigami
```

With the skills CLI, for Claude Code and other agents that read SKILL.md:

```bash
npx skills add omnigami-ai/chat-launch
```

Or copy `skills/chat-launch/` into your agent's skills folder (for Claude Code, `~/.claude/skills/chat-launch/`). Then ask:

```
Make a chat launch video for https://your-product.com
```

## What it runs

The skill works on your computer. It runs the Node scripts in `skills/chat-launch/scripts/`: they open your product's pages in a local headless browser to capture its real screens, then render the film with that browser and ffmpeg, writing MP4s and an editable HTML film to your project. It sends nothing to omnigami or anyone else, and uses no network beyond loading your own product's pages and the fonts and assets in this folder.

## You need

- Claude Code with Opus 5.5
- Node 20 or later
- ffmpeg
- Chrome, Chromium, Edge or Brave

None beyond your Claude plan’s usage. Node, ffmpeg and the browser are free.

## Licence

Free to use. Use the films and anything else the skill makes for anything, commercial work included. Don't redistribute the skill. See [LICENSE.md](LICENSE.md). The bundled fonts keep their own licence (SIL Open Font License, beside them in `reference/assets/fonts/`).

## Credits

Style inspired by @twoclipping’s video (https://x.com/twoclipping/status/2104446706741825818); @twoclipping didn’t make or endorse this skill. Its example shows Ostlery, a fictional company made for omnigami’s examples, with sample data.

omnigami is not affiliated with Anthropic. More skills at [omnigami.ai](https://omnigami.ai).
