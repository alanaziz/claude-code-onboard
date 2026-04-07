# Claude Code Onboard

10-minute guided onboarding for Claude Code. One command builds your entire AI workspace.

## What It Does

Run `/onboard` and in 10 minutes you'll have:

- **Voice DNA** — Claude learns how you actually write by scanning your emails and messages, then builds a detailed voice profile with real writing samples
- **Context files** — who you are, how you work, your full tool stack and preferences
- **Project consolidation** — existing project folders from across your computer, moved into one organised workspace
- **Self-correcting rules engine** — your workspace gets smarter every time Claude makes a mistake
- **Context-first AI** — Claude checks your files and tools before asking you questions

## How It Works

1. **Connect your tools** — step-by-step guidance to link Gmail, Google Drive, Calendar, Notion, and Slack via the Claude Desktop app
2. **Deep discovery scan** — digs through your sent emails, messages, and docs to learn your writing style and find existing business context
3. **Guided interview** — 14 focused questions about you, your voice, your workflow, your tools, and your existing projects. Every question comes with rich examples so you're never staring at a blank prompt
4. **Project migration** — finds your scattered project folders and organises them into one workspace
5. **Workspace setup** — generates CLAUDE.md with context-first philosophy and self-correcting rules engine

## Installation

```
/plugin marketplace add aiwithremy/claude-code-onboard
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
├── active/                            # All generated output goes here
└── [your projects]                    # Existing folders migrated in
```

## Requirements

- Claude Code CLI (or Claude Code in VS Code / JetBrains / Desktop)
- For the discovery scan: Claude Desktop app with Gmail, Calendar, etc. connected (optional but recommended)

## Author

AI with Remy — [aiwithremy.com](https://aiwithremy.com)

## License

MIT
