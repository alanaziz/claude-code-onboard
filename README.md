# Claude Code Onboard

Guided onboarding for Claude Code. One command builds a personalized AI workspace that knows your business and writes in your voice.

## What It Does

Run `/onboard` and you'll have:

- **Voice DNA** — Claude learns how you actually write by scanning your emails and messages, then builds a detailed voice profile with real writing samples
- **Context files** — who you are, how you work, your full tool stack and preferences
- **One workspace per brand** — each business or persona gets its own `OS-[Name]` folder, so you can run `/onboard` again for a new venture without touching the others
- **A CLAUDE.md that stays out of the way** — short, points at your context files, and puts the one rule you most need followed front and centre

## How It Works

1. **Connect your tools** — step-by-step guidance to link Gmail, Google Drive, Calendar, Notion, and Slack via the Claude Desktop app
2. **Deep discovery scan** — digs through your sent emails, messages, and docs to learn your writing style and find existing business context
3. **Guided interview** — a focused set of questions about you, your voice, and your workflow. Every question comes with rich examples so you're never staring at a blank prompt
4. **Workspace setup** — asks what brand/business this workspace is for, then generates a lean CLAUDE.md pointing at your context files, with the one rule that matters most called out

## Installation

```
/plugin marketplace add alanaziz/claude-code-onboard
```

## Usage

Open Claude Code anywhere, then run:

```
/onboard
```

Follow the guided flow. That's it.

### Updating Later

To update specific parts of your workspace:

```
/update-context
```

This lets you refresh individual sections (about me, voice DNA, working style) without re-doing everything.

## What Gets Created

```
~/Desktop/OS-[Name]/
├── CLAUDE.md                          # Master instructions — short, points at context/, one rule up front
├── context/
│   ├── about-me.md                    # Identity, role, business, expertise
│   ├── voice-dna.md                   # Writing style, tone, samples, anti-patterns
│   └── working-style.md              # Output prefs, rules, tasks, full tool stack
└── active/                            # All generated output goes here
```

Each brand or venture gets its own `OS-[Name]` folder on the Desktop — run `/onboard` again for a new one.

## Requirements

- Claude Code CLI (or Claude Code in VS Code / JetBrains / Desktop)
- For the discovery scan: Claude Desktop app with Gmail, Calendar, etc. connected (optional but recommended)

## Author

Alan Aziz — [alanaziz.com](https://alanaziz.com)

Forked from [aiwithremy/claude-code-onboard](https://github.com/aiwithremy/claude-code-onboard) under the MIT license.

## License

MIT
