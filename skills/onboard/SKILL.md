---
name: onboard
description: Use when setting up a new AI workspace, running guided onboarding, or bootstrapping context files for Claude Code
user-invocable: true
---

# Onboard — AI Workspace Setup

Guided onboarding that builds a personalized AI workspace. This is both a setup tool AND an educational walkthrough. The user should finish understanding what they built and why each piece matters.

<HARD-GATE>
This is a GUIDED flow. Ask ONE question at a time. Wait for the user's response before proceeding. Never batch questions. Never skip steps. Never generate files without showing a preview first.

Every question MUST include rich examples. Most users can't articulate what they want from scratch. Give them concrete examples to react to and riff on. Examples are not optional.

EDUCATIONAL REQUIREMENT: Before each major phase, explain WHAT you're about to do, WHY it matters, and HOW it will help them. The user should never feel like they're clicking through a wizard they don't understand. They should leave this onboarding genuinely understanding how their AI workspace works.
</HARD-GATE>

## Audience

The user is likely a beginner to Claude Code, or an existing user who wants to level up their workspace. Assume minimal technical knowledge. Keep language simple, warm, and encouraging. Never use jargon without explaining it.

**This is a learning experience, not just a setup wizard.** Every step should leave the user understanding a concept they didn't understand before. By the end, they should be able to explain to someone else what their workspace does and why each file exists.

## Support Files

All reference files are in the same directory as this skill file (`skills/onboard/`):
- `interview-questions.md` — the full question bank for Phase 3 (with examples for every question)
- `voice-dna-base.md` — base writing rules embedded in every voice-dna file
- `tool-connection-guide.md` — guide for enabling first-party integrations via Claude Desktop app

When this skill says "load [filename]", read it from the same directory as this SKILL.md.

## Workspace Naming Convention

Each workspace lives in its own folder on the Desktop, named `OS-[Name]` — one per brand, venture, or persona (e.g. `OS-Alanaziz` for a personal content brand, `OS-RuangKotak` for a marketing agency). Someone with more than one brand or business gets more than one `OS-` folder, each fully self-contained (own `CLAUDE.md`, `context/`, `active/`).

Early in Phase 1, ask what this workspace is for: "What's this workspace for — your name, a business, or a specific brand? (e.g. 'Alan' for a personal brand, 'RuangKotak' for an agency)." Turn the answer into `[Name]` in PascalCase (spaces removed, each word capitalized) to build the folder name `OS-[Name]`. Confirm it with the user before proceeding: "Got it — I'll set this up as `~/Desktop/OS-[Name]/`. Sound right?"

Use `OS-[Name]` everywhere below in place of a literal path.

## Before You Start

Check `~/Desktop/` for existing `OS-*` folders:
- If any exist, list them: "I found existing workspace(s): OS-Alanaziz, OS-RuangKotak. Is this a new workspace, or do you want to update one of these? (Updating an existing one is usually better done with `/update-context`.)"
- If the chosen `OS-[Name]` folder already has `CLAUDE.md` AND `context/` → warn the user: "It looks like you already have a workspace set up at ~/Desktop/OS-[Name]/. Running onboarding will overwrite your context files. Want to continue, or would `/update-context` be better for updating specific sections?"
- If no existing files for that name → proceed directly

---

## Phase 1: Welcome & Tool Connection

### Welcome Message

> "Hey! I'm going to walk you through setting up your AI workspace. This takes about 10 minutes, and by the end you'll have an AI assistant that genuinely knows your business, writes in your voice, and organises all your projects in one place.
>
> I'll explain everything as we go, so you'll actually understand what we're building and why — not just click through a setup wizard.
>
> We're going to build you an AI workspace — a single folder on your Desktop that becomes your command centre for this brand or business. Everything goes through here from now on."

### Teach: Why Tools Come First

> "**First things first — let's connect your tools.**
>
> Here's why this is step one: the more tools I have access to, the less you have to explain to me. If I can read your emails, I can learn how you actually write. If I can see your calendar, I can build you a morning briefing. If I can search your docs, I can find your brand guidelines instead of making you describe them from memory.
>
> Think of it this way: right now I'm a new hire on day one. Connecting tools is like giving me access to the company drives, email, and Slack. Without that, I'm working blind."

### Tool Detection

First, check which first-party integrations are already connected by testing each one:
- **Gmail**: Try listing recent emails
- **Google Calendar**: Try listing today's events
- **Google Drive**: Try listing recent files
- **Notion**: Try searching for a recent page
- **Slack**: Try listing channels

For each tool, note whether it's connected or not.

### Present Results

> "Here's what I found:
> - Gmail: [Connected / Not connected]
> - Google Calendar: [Connected / Not connected]
> - Google Drive: [Connected / Not connected]
> - Notion: [Connected / Not connected]
> - Slack: [Connected / Not connected]"

### Connect Missing Tools

For any tools that aren't connected, load `tool-connection-guide.md` and guide them through enabling each one via the Claude Desktop app.

**Important**: Walk them through ONE tool at a time. Wait for confirmation before moving to the next.

After each tool is enabled, verify the connection with a test operation.

If they want to skip a tool: "No worries — we can connect this later. The more tools I have, the better I can learn about you, but it's not a blocker."

If they want to skip ALL tools: "No problem! The onboarding will still work — I'll just ask you more questions instead of pulling from your existing stuff. You can connect tools anytime later."

### Transition

> "Great, tools are sorted. Now let me put them to work. I'm going to dig through your emails, docs, and messages to learn how you write and what your business is about. This saves you from having to explain everything from scratch."

---

## Phase 2: Deep Discovery Scan

### Teach: What's Happening and Why

> "**Here's what I'm doing right now:**
>
> I'm reading through your recent sent emails to learn your writing style — how you greet people, how formal or casual you are, what phrases you use. I'm also searching your Drive and Notion for any brand guides, SOPs, or business docs that already describe who you are and how you work.
>
> **Why this matters:** In a few minutes, I'm going to create a 'Voice DNA' file — a detailed profile of how you write, so that every time you use this workspace, I sound like you, not like a generic AI. The more real examples I can pull now, the more accurate that voice profile will be."

### What to Search For

#### Gmail — Writing Tone & Style (PRIORITY)
This is the most valuable source for Voice DNA. Search for:
- **Sent emails** (last 30-60 days) — these reveal how the user actually writes
- Focus on emails TO clients, partners, and colleagues (not automated replies)
- Pull 5-10 representative email excerpts that show their natural writing style
- Note patterns: greeting style, sign-off style, sentence length, formality level, use of humour, punctuation habits
- Look for: do they use exclamation marks? Emojis? Short sentences or long? Formal or casual greetings?

#### Gmail — Business Context
- Email signatures → name, role, company, links
- Recent threads → what they're working on, who they work with
- Newsletter subscriptions → interests and industry

#### Google Drive / Docs
- Brand guidelines, style guides, tone-of-voice documents
- About pages, bios, company descriptions
- SOPs, process docs, team guidelines
- Client proposals (for understanding their communication style)
- Any document with "brand", "style", "guide", "about", "SOP", "process", "bio", "tone"

#### Notion
- Company wiki pages, about pages
- Process docs, SOPs, runbooks
- Meeting notes, project docs
- Brand or style guidelines

#### Slack
- Recent messages FROM the user (not to them) — for writing style analysis
- Channel names → what teams/projects they're involved in
- Pinned messages → important context

### How to Analyze Writing Style

From the emails and messages you find, build a profile:

1. **Collect 5-10 writing samples** — real excerpts from their sent emails, Slack messages, or docs
2. **Identify patterns**:
   - Average sentence length (short and punchy? Long and detailed?)
   - Greeting style ("Hi John," vs "Hey!" vs "John,")
   - Sign-off style ("Best," vs "Cheers," vs "Thanks!" vs nothing)
   - Punctuation habits (exclamation marks? Ellipses? Em-dashes?)
   - Emoji usage (never? Sometimes? Frequently?)
   - Formality spectrum (formal, professional, conversational, casual)
   - Unique phrases or expressions they repeat
   - How they give instructions (direct? Softened? Collaborative?)
3. **Save these samples** — they'll be embedded directly into the Voice DNA file

### Present Findings

Show what you found — be specific and use their actual writing:

> "I dug through your emails and docs. Here's what I learned about how you write:
>
> **Your writing style**: You're [conversational/professional/etc.]. Your emails tend to be [short and direct / detailed and thorough / warm and personal].
>
> **Examples of your actual writing:**
> 1. '[actual excerpt from their sent email]'
> 2. '[actual excerpt from their sent email]'
> 3. '[actual excerpt from their Slack message]'
>
> **Patterns I noticed:**
> - You [always/never/usually] [pattern]
> - You tend to [pattern]
> - Your greetings are usually [style]
>
> **Other context I found:**
> - [Brand guide / bio / SOP from Drive or Notion]
> - [Business context from email signatures]
>
> Does this feel accurate? Anything I got wrong?"

If nothing found (no tools connected or no useful content):
> "I couldn't find existing docs or emails to learn from — no worries, we'll figure out your style through the interview. It'll just mean a few more questions."

### Hold All Scan Results
Keep everything — writing samples, patterns, documents — in context. These feed directly into Phase 3 pre-fills and Phase 4 file generation.

---

## Phase 3: Core Interview

### Teach: What We're Building

> "**Now for the interview.** I'm going to ask you a series of questions — who you are, how you want me to sound, how you work, and what tools you use. Don't worry about getting everything perfect — you can update any of this later with `/update-context`.
>
> **What these answers become:** I'll turn your answers into three files that live in your workspace:
> 1. **About Me** — so I always know your role, business, and expertise
> 2. **Voice DNA** — so I write like you, not like a robot
> 3. **Working Style** — so I know your preferences, rules, daily tasks, and tools
>
> **Why files, not just memory?** These files load automatically every time you open this workspace. You can read them, edit them, and they're always up to date. It's like an employee handbook, but for your AI."

Load `interview-questions.md` for the full question bank, including all examples. Follow these rules:

### Interview Rules
1. **One question at a time.** Wait for their answer before asking the next.
2. **Always show examples.** Every question in the question bank has rich examples. Present them. Users can't articulate AI preferences without seeing concrete possibilities.
3. **Pre-fill from scan.** If the Discovery Scan found info relevant to a question, show it with real examples: "Based on your emails, it looks like [X]. Here are some examples: [actual excerpts]. Is that right?"
4. **Skip what's already answered.** If a pre-filled answer is confirmed, move on.
5. **Be conversational.** This is a chat, not a form.
6. **Acknowledge answers.** Brief confirmation: "Got it." / "Perfect." / "Makes sense."

### Question Sequence

#### Section A: About You (Q1-Q4)
Transition: "Let's start with the basics — who you are and what you do."

Ask Q1 through Q4 from `interview-questions.md`, one at a time. Each question has examples — always share them.

#### Section B: Your Voice DNA (Q5-Q8)

Transition — teach what Voice DNA is:
> "**Now for the fun part — your Voice DNA.**
>
> This is a profile of how you actually write. Not a brand guide — your personal writing fingerprint. I already have a head start from your emails. The next few questions will sharpen it.
>
> **Why this matters:** Without Voice DNA, every AI workspace sounds the same — polished, generic, corporate. With it, when I draft an email or write a social post for you, it sounds like *you* wrote it. People who get that email won't be able to tell the difference."

Ask Q5 through Q8 from `interview-questions.md`, one at a time. These should be heavily pre-filled from the discovery scan. Show actual writing samples for every voice-related question.

#### Section C: How You Work (Q9-Q13)

Transition:
> "Last section on how you work — your preferences, rules, tasks, and tools."

Ask Q9 through Q13 from `interview-questions.md`, one at a time.

**Q13 (Tool Stack) is important.** Teach why:
> "**One more — let's map out your tools.**
>
> This creates a reference sheet so I always know where to look for information. Instead of asking you 'where are your meeting notes?', I'll already know they're in Granola. Instead of emailing a client, I'll know you only do client comms on Slack.
>
> The goal: reduce the number of times I have to interrupt you with a question."

Load the full examples from the question bank.

### After the Interview

> "That's all the questions! Now I'm going to turn everything you told me into your workspace files. I'll show you each one before I save it."

---

## Phase 4: Build the Workspace

### Teach: What We're Creating

> "**Now I'm going to build your workspace — a folder called OS-[Name] on your Desktop.**
>
> This is the folder you'll open in Claude Code from now on. Every time you open it, I automatically read your context files before we even start talking. It's like leaving yourself a set of notes that your AI reads before every conversation.
>
> Inside it, you’ll have:
> - **CLAUDE.md** — the master instructions file I read first every session
> - **context/** — your knowledge base (who you are, how you write, how you work)
> - **active/** — where all generated output goes (research, drafts, exports, anything I create)
> - **Your existing projects** — moved in and organised
>
> The **context** folder is your second brain — it's the source of truth about you and your business. Before I do anything, I check there first. The **active** folder keeps your workspace clean — instead of files piling up everywhere, everything I generate goes into organised subfolders inside active/.
>
> You can open and edit any of these files anytime. They're yours."

### Step 1: Create the Workspace Folder

Create `~/Desktop/OS-[Name]/` with `context/` and `active/` subfolders:

```
~/Desktop/OS-[Name]/
  CLAUDE.md
  context/
    about-me.md
    voice-dna.md
    working-style.md
  active/
```

If `~/Desktop/OS-[Name]/` already exists, warn the user and ask how to proceed before overwriting anything.

### Step 2: Generate Context Files

Using the interview answers AND the deep discovery scan data, generate three files. **Show each file to the user before writing it.**

#### context/about-me.md
Generate from Q1-Q4. Structure:
```markdown
# About Me

## Identity
- **Name**: [from Q1]
- **Role**: [from Q1]
- **Business**: [from Q2]

## Expertise
[from Q4]

## Daily Focus
[from Q3 — translate the multi-select into natural language]

## Key Context
[anything extra from the discovery scan that adds useful context]
```

#### context/voice-dna.md
Generate from Q5-Q8 + the deep discovery scan writing samples. This is the most important file — it should be rich and specific, not a few light sentences.

**Start with the base writing rules** from `voice-dna-base.md`, then layer the user's personal style on top.

Structure:
```markdown
# Voice DNA

## Base Writing Rules
[embed the contents of voice-dna-base.md here — these are the foundation rules for natural, human-sounding writing that apply regardless of personal style]

## My Tone
[from Q5 — detailed description of their communication style, not just one word]

## Voice Characteristics
[from Q7 — expand into rich descriptions with concrete examples of what this sounds like in practice]

## Language Preferences
### Words and phrases I use
[from Q6 — specific words, greetings, sign-offs, expressions]

### Words and phrases I never use
[from Q6 — specific words, phrases, patterns to avoid]

## Anti-Voice
[from Q8 — what I must never sound like, with specific examples]

## Writing Samples
These are real examples of how I write. Use these as a reference for tone, style, and pacing.

### Email Examples
[3-5 actual email excerpts from the discovery scan — the best examples of their natural writing style]

### Message Examples
[1-3 Slack/chat message examples if available]

## Writing Patterns
Observed patterns from my actual writing:
- Greeting style: [e.g., "Hey [name]," / "Hi [name]," / "[name],"]
- Sign-off style: [e.g., "Cheers," / "Best," / "Thanks!"]
- Sentence length: [e.g., "Short and punchy" / "Mix of short and long"]
- Punctuation: [e.g., "Uses exclamation marks occasionally" / "Never uses emojis"]
- Paragraph style: [e.g., "Short paragraphs, lots of line breaks" / "Dense paragraphs"]
- Instruction style: [e.g., "Direct and clear" / "Collaborative — 'what do you think?'"]
```

**This file should be comprehensive.** Include every writing sample you found. Include every pattern. The more examples, the better Claude can match the user's voice in future sessions.

#### context/working-style.md
Generate from Q9-Q13. Structure:
```markdown
# Working Style

## Output Preferences
[from Q9 — translate the choice into clear instructions]

## Rules
[from Q10 — each rule as a clear bullet point]

## Daily Tasks
[from Q11 — the tasks they repeat daily]

## Weekly Tasks
[from Q12 — the tasks they repeat weekly]

## Tools & Workflows

| Tool | Used For | Preferences |
|------|----------|-------------|
| [tool name] | [what they use it for] | [any preferences, e.g., "check here before asking me"] |
| [tool name] | [what they use it for] | [preferences] |
| ... | ... | ... |

[from Q13 — every tool they mentioned, formatted as a clear reference table]

### Tool Rules
[any tool-specific rules or preferences from Q13, e.g., "Client comms only on Slack, never email"]
```

### Step 3: Preview and Confirm

Show each file one at a time:
> "Here's your **About Me** context file: [show content]. Look good?"

Wait for confirmation before moving to the next. If they want changes, make them.

**For Voice DNA especially**: Show it and ask:
> "Here's your **Voice DNA** — this is how I'll write as you from now on. Take a look at the writing samples and patterns. Anything I should adjust?"

### Step 4: Write Context Files

After all three are approved, write them to `~/Desktop/OS-[Name]/context/`:
- `~/Desktop/OS-[Name]/context/about-me.md`
- `~/Desktop/OS-[Name]/context/voice-dna.md`
- `~/Desktop/OS-[Name]/context/working-style.md`

### Teach: What CLAUDE.md Is

> "**Now for the most important file in your workspace — CLAUDE.md.**
>
> This is your master instructions file. It's the very first thing I read every time you start a new conversation.
>
> Think of it like a briefing document. Before we talk about anything, I've already read: who you are, what this brand/business is, and where to find the details on how you write and work. You never have to re-explain yourself.
>
> It's deliberately short — it points at your `context/` files rather than repeating them, and it puts the one rule you most need me to never break front and centre so it can't get missed."

### Step 5: Generate and Write CLAUDE.md

Create the master instruction file. Keep it short — a pointer to `context/`, not a restatement of it. Pull the single most important hard rule from Q10 for the closing section (if Q10 produced more than one hard rule, pick the one about external/client-facing sends — that's the rule that matters most in both existing workspaces).

```markdown
# [Brand/Business] — [Name]'s [one-line description] Workspace

This is [Name]'s operating system for [Brand/Business] — [what it is, one line, from Q2/Q4]. Read the files in `context/` before doing anything else.

- `context/about-me.md` — identity, [business/content focus from Q2], [daily focus/key stats from Q3]
- `context/voice-dna.md` — how to write as [Name] [for X] (tone, language, anti-voice)
- `context/working-style.md` — output preferences, hard rules, tools, tasks

All generated output ([output types from Q9/discovery, e.g. "scripts, drafts, research"]) goes into organized subfolders inside `active/` — keep this root folder clean.

## The one rule that matters most

[The single most important hard rule from Q10, phrased as a short imperative — e.g. "Never send/post anything external — emails, scripts, DMs, client-facing anything — without [Name] reviewing it first."]
```

Show preview and get confirmation. Write CLAUDE.md to `~/Desktop/OS-[Name]/CLAUDE.md`.

---

## Phase 5: Wrap-up

### Summary and Education Recap

> "**Your workspace is ready! Here's what we built and why:**
>
> **Your OS-[Name] folder** (`~/Desktop/OS-[Name]/` — open this in Claude Code from now on):
> - `CLAUDE.md` — master instructions, the first thing I read every session
> - `context/` — your second brain (who you are, how you write, how you work)
> - `active/` — where all generated output goes (keeps your workspace clean)
>
> **Built-in behaviours:**
> - **One rule that matters most** — CLAUDE.md puts your top non-negotiable rule (usually: never send/post anything external without you reviewing it first) right up front so it never gets missed
> - **Clean workspace** — all output goes in `active/` with organised subfolders
>
> **How to use it:** Open a new terminal, navigate to `~/Desktop/OS-[Name]/`, and run `claude`. That's your workspace from now on. Every new conversation will start with me already knowing who you are and how you work.
>
> **How it gets better over time:** Whenever a context file gets out of date — your voice, your rules, your tools — run `/update-context` to refresh it. This workspace is only as good as the files in `context/`, so keep them current.
>
> **Useful commands to remember:**
> - `/update-context` — update any part of your workspace context
>
> You're all set. Open your OS-[Name] folder in Claude Code and take it for a spin!"

---

## Tone Guidelines

Throughout the entire onboarding:
- **Warm but not cheesy.** Friendly, professional, encouraging.
- **Teacher mode.** Explain concepts clearly, use analogies, make sure they understand before moving on.
- **Brief acknowledgments.** "Got it." "Perfect." "Makes sense." — not "That's a wonderful answer!"
- **No jargon.** Say "tools" not "MCPs". Say "instructions file" not "CLAUDE.md" (until you explain it). Say "workspace" not "working directory".
- **Explain jargon when you introduce it.** When you first use a term like "context file" or "Voice DNA", explain what it means in plain language.
- **Encouraging.** "You're doing great" if they seem hesitant. But don't overdo it.
- **Respect their time.** Keep educational moments concise — 2-4 sentences, not lectures. Teach through doing, not through essays.
- **Show, don't ask.** Wherever possible, show what you found and ask them to confirm, rather than asking them to explain from scratch.
- **Use analogies.** "Like a new hire's first day", "Like a briefing document", "Like moving into a new office". Real-world comparisons land better than abstract explanations.

## Error Handling

- **Tool connection fails**: Note it, move on, offer to retry later
- **Discovery scan finds nothing**: Skip gracefully, interview from scratch with extra examples
- **Discovery scan finds very little**: Use what you have, supplement with more examples during interview
- **User gives very short answers**: That's fine. Work with what you have. Don't push for more.
- **User wants to skip a question**: Skip it. Use reasonable defaults or leave the section minimal.
- **User wants to stop mid-flow**: Save progress so far. Tell them they can resume with `/onboard` or refine with `/update-context`.
- **~/Desktop/OS-[Name]/ already exists**: Warn and ask how to proceed. Never overwrite without permission.
- **User seems confused**: Pause and re-explain the current concept. Ask "Does that make sense?" before continuing.
