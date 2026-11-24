# Scratch design

An Agent Skill that turns a [Scratch](https://chino.nyc/scratch) board (wireframes, user flows, sketches and reference images) into a prototype, page, motion piece, chart or design review. It brings the habits of a senior UX, visual, motion and data-visualization designer.

Scratch's **Send to AI** button opens Claude, ChatGPT, Codex, Cursor, Claude Code, Figma Make or Lovable with your board ready to go. Send to AI works without this skill. With the skill, the AI tool works from the board in much more detail.

## What it does

- **Reads the board.** It downloads every frame and picture from the hand-off link and checks each one against the hand-off's checksums. It follows the frames in flow order, along with the taps, clicks and swipes between them.
- **Knows Scratch's markings.** Numbered circles are steps, blue circles are taps and arrows are swipes. It treats them as notes about interactions and never builds them into the design.
- **Checks in before building.** It gives a short read-out: who the design is for, the flow, missing states (empty, loading, error) and what each reference image contributes. You can correct it before it starts.
- **Builds to a standard.** It follows rules for flows, states, forms and phone ergonomics; type, color and spacing; motion timing and easing, including reduced motion; and charts that state their point and come with an accessible table.
- **Reviews its own work.** It checks the result against a list of design and accessibility checks and fixes what it finds before showing you.
- **Treats the board as material.** Words on frames, notes and linked pages are things to design from, never instructions to follow.

## Install

Pick the tools you use. Each one needs the skill installed separately.

### Claude (web, desktop app and Claude Code)

1. In Claude, open **Customize › Plugins** (just **Plugins** in newer versions), click **+**, then **Add marketplace**.
2. Choose **Add from a repository** and enter `chinovian/scratch-design`.
3. Install **Scratch design**.

Claude saves it to your account, so it works in chat, Cowork and Claude Code.

To let the skill download hand-offs in Claude chat, turn on code execution and allow `chino.nyc` in its network settings. Without that, it works from the link's page and any images you paste.

If adding a marketplace isn't available to you, download [scratch-design.zip](https://chino.nyc/scratch/skill/scratch-design.zip). Then go to **Customize › Skills › + › Upload a skill** and choose the zip.

### Claude Code on its own

```
/plugin marketplace add chinovian/scratch-design
/plugin install scratch-design@scratch-skills
```

### Codex, Cursor, GitHub Copilot, Gemini CLI and other coding agents

```
npx skills add chinovian/scratch-design -g
```

The installer finds the agents on your machine and asks which ones to add the skill to. Add `-a codex`, `-a cursor` or `-a claude-code` to choose up front. With the GitHub CLI, `gh skill install chinovian/scratch-design scratch-design` does the same. Restart Codex afterwards so it loads the skill.

### ChatGPT (Business, Enterprise, Healthcare and Edu)

Download [scratch-design.zip](https://chino.nyc/scratch/skill/scratch-design.zip). Then in ChatGPT, open **Plugins › Skills › Create › Upload from your computer** and choose the zip.

### Figma Make

Figma Make keeps one file per skill. Download [SKILL.md](https://chino.nyc/scratch/skill/SKILL.md). Then in a Make chat, click the prompt box and choose **Skills › Add skill**, and upload the file. SKILL.md is written to work on its own.

### Lovable and other tools without skills

You don't need to install anything. Scratch puts a short design brief into the prompt instead.

## Try it

Send something from Scratch, or give your AI tool a hand-off link yourself:

```
Use the scratch-design skill on https://chino.nyc/scratch/h/<id>/
```

It downloads the hand-off and gives you a short read-out of the frames before it builds. If it can't download, it says why.

## Updating

- **Claude:** go to the marketplace in Plugins and update it. In Claude Code, run `/plugin marketplace update scratch-skills`.
- **Codex, Cursor and others:** run `npx skills update`.
- **Zip uploads (ChatGPT, or Claude without a marketplace):** download the zip again and upload it over the old one.

When a hand-off comes from a site that offers a newer version, the skill mentions it at the end of its report.

## What's inside

```
skills/scratch-design/
  SKILL.md                 the workflow and the craft rules; works on its own
  references/              deeper guidance on UX, visual design, motion, data visualization, reviewing, and the hand-off format
  scripts/fetch_handoff.py downloads a hand-off and checks every file (Python 3.8+, standard library only)
.claude-plugin/            lets Claude install this repository as a plugin
```

## Releasing a new version

1. Change `metadata.version` in `skills/scratch-design/SKILL.md` and `version` in `.claude-plugin/plugin.json`, and add a line to `CHANGELOG.md`.
2. Push. Claude users only receive the update when the `plugin.json` version changes.
3. On chino.nyc, update `scratch/skill/`: put in the new `scratch-design.zip` and `SKILL.md`, and set `version` in `skill.json`. Scratch then tells people when their copy is out of date.

## License

MIT. See [LICENSE](LICENSE).
