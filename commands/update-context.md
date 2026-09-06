---
description: "Update specific parts of your workspace context"
---

Check `~/Desktop/` for existing `OS-*` folders. If there's more than one, ask which workspace this update is for. If there's exactly one, use it. If none exist, tell the user to run `/onboard` first.

Ask the user which section they want to update:

1. **About me** — re-interview identity, role, business, expertise → regenerate `~/Desktop/OS-[Name]/context/about-me.md`
2. **Voice DNA** — re-scan emails/messages for writing samples, re-interview tone and style → regenerate `~/Desktop/OS-[Name]/context/voice-dna.md`
3. **Working style** — re-interview output preferences, rules, tasks, tool stack → regenerate `~/Desktop/OS-[Name]/context/working-style.md`
4. **Everything** — re-run the full onboarding (same as `/onboard`)

For options 1-3: read the existing file first, show the user what's currently there, then use the `claude-code-onboard:onboard` skill's support files to guide the update:
- **About me** (option 1): load Section A from `interview-questions.md` for targeted questions
- **Voice DNA** (option 2): re-run the deep discovery scan for fresh writing samples, then load Section B from `interview-questions.md`. Embed base rules from `voice-dna-base.md`
- **Working style** (option 3): load Section C from `interview-questions.md` (includes tool stack quiz at Q13)

Show the current content, ask targeted questions from the question bank (always include examples), then regenerate only the selected file. Preview changes before writing.

For option 4: use the `claude-code-onboard:onboard` skill to run the full flow.

After updating, also check if `~/Desktop/OS-[Name]/CLAUDE.md` needs changes to reflect the updates (e.g., new tools, changed rules).
