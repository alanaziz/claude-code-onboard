# Claude Code Onboard

Guided onboarding for Claude Code. One command builds a personalized AI workspace that knows your business and writes in your voice.

## What It Does

Run `/onboard` and you'll have:

- **Voice DNA** — Claude learns how you actually write by scanning your emails and messages, then builds a detailed voice profile with real writing samples
- **Context files** — who you are, how you work, your full tool stack and preferences
- **Self-correcting rules engine** — your workspace gets smarter every time Claude makes a mistake
- **Context-first AI** — Claude checks your files and tools before asking you questions

## How It Works

1. **Connect your tools** — step-by-step guidance to link Gmail, Google Drive, Calendar, Notion, and Slack via the Claude Desktop app
2. **Deep discovery scan** — digs through your sent emails, messages, and docs to learn your writing style and find existing business context
3. **Guided interview** — a focused set of questions about you, your voice, and your workflow. Every question comes with rich examples so you're never staring at a blank prompt
4. **Workspace setup** — generates CLAUDE.md with context-first philosophy and self-correcting rules engine

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
~/Desktop/OS/
├── CLAUDE.md                          # Master instructions + self-correcting rules engine
├── context/
│   ├── about-me.md                    # Identity, role, business, expertise
│   ├── voice-dna.md                   # Writing style, tone, samples, anti-patterns
│   └── working-style.md              # Output prefs, rules, tasks, full tool stack
└── active/                            # All generated output goes here
```

## Requirements

- Claude Code CLI (or Claude Code in VS Code / JetBrains / Desktop)
- For the discovery scan: Claude Desktop app with Gmail, Calendar, etc. connected (optional but recommended)

## Author

Alan Aziz — [alanaziz.com](https://alanaziz.com)

Forked from [aiwithremy/claude-code-onboard](https://github.com/aiwithremy/claude-code-onboard) under the MIT license.

## License

MIT
