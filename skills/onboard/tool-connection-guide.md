# Tool Connection Guide

Reference document for guiding users through connecting their tools via the Claude Desktop app. First-party integrations enabled in Claude Desktop are automatically available in Claude Code CLI sessions.

## How to Use This Guide

For each tool the user wants to connect:
1. Read the relevant section below
2. Walk them through step-by-step
3. After they say it's connected, verify with the test operation in Claude Code
4. If the test fails, troubleshoot briefly. If it still fails, note it and move on

Keep instructions conversational, not robotic. One step at a time, wait for confirmation before the next.

## Important: How This Works

First-party integrations are connected through the **Claude Desktop app**, not through Claude Code directly. Once connected in Desktop, the tools become available in Claude Code CLI sessions automatically.

The user needs:
1. The **Claude Desktop app** installed on their computer
2. A Claude account (same one they use for Claude Code)

If they don't have the Desktop app: "You'll need the Claude Desktop app to connect tools. You can download it from claude.ai/download. Once installed, sign in with the same account you use for Claude Code."

---

## Gmail

### Connection Steps
1. Open the **Claude Desktop app**
2. Go to **Settings** (gear icon or Claude menu → Settings)
3. Find the **Integrations** or **Connected Apps** section
4. Look for **Gmail** and click **Connect**
5. A browser window will open — sign in to your Google account
6. Grant the requested permissions (read and send access)
7. Return to Claude Desktop — Gmail should show as connected

### Verification Test (in Claude Code)
Try listing recent emails:
- Search for recent inbox messages
- If you can see subject lines, the connection works

### Common Issues
- **"This app isn't verified"**: Click "Advanced" then "Go to [app name]" to proceed
- **Multiple email accounts**: Connect your primary business email first. You can add more later
- **Not showing in Claude Code**: Try starting a new Claude Code session after connecting

---

## Google Calendar

### Connection Steps
1. Open the **Claude Desktop app**
2. Go to **Settings** → **Integrations**
3. Look for **Google Calendar** and click **Connect**
4. May share the same auth as Gmail if already connected to Google
5. Grant calendar access
6. Return to Claude Desktop — Calendar should show as connected

### Verification Test (in Claude Code)
Try listing upcoming events:
- Check today's or this week's calendar events
- If you can see event titles and times, the connection works

### Common Issues
- **No events showing**: Check that the calendar you use is the primary calendar on the connected account
- **Shared calendars**: Shared/team calendars may not appear. Focus on the primary calendar for now

---

## Google Drive / Docs

### Connection Steps
1. Open the **Claude Desktop app**
2. Go to **Settings** → **Integrations**
3. Look for **Google Drive** and click **Connect**
4. Sign in to your Google account and grant access
5. Return to Claude Desktop — Google Drive should show as connected

### Verification Test (in Claude Code)
Try listing recent files:
- Search for a recent document from Google Drive
- If you can see file names, the connection works

### Common Issues
- **"Access denied"**: You may need to use a personal Google account rather than a managed workspace account with restricted permissions
- **Wrong account**: Disconnect, then reconnect and choose the right Google account

---

## Notion

### Connection Steps
1. Open the **Claude Desktop app**
2. Go to **Settings** → **Integrations**
3. Look for **Notion** and click **Connect**
4. A Notion authorization page will open
5. Select which Notion workspace to connect
6. Choose which pages/databases to grant access to (you can select all or specific ones)
7. Click **Allow access**
8. Return to Claude Desktop — Notion should show as connected

### Verification Test (in Claude Code)
Try searching for a recent page:
- Search Notion for a page you know exists
- If you can see page titles, the connection works

### Common Issues
- **"No workspaces available"**: Make sure you're logged into the right Notion account in your browser
- **Can't see certain pages**: During authorization, you need to explicitly select which pages to share. Reconnect and select more pages if needed
- **Slow response**: Notion API can be slow with large workspaces. This is normal

---

## Slack

### Connection Steps
1. Open the **Claude Desktop app**
2. Go to **Settings** → **Integrations**
3. Look for **Slack** and click **Connect**
4. Slack authorization will open — select your workspace
5. Review and approve the permissions
6. Return to Claude Desktop — Slack should show as connected

### Verification Test (in Claude Code)
Try listing recent channels:
- Search for a channel you know exists
- If you can see channel names, the connection works

### Common Issues
- **"You don't have permission"**: You may need workspace admin approval. Ask your Slack admin to approve the integration
- **Wrong workspace**: Disconnect and reconnect, making sure to select the correct workspace
- **Can't see DMs**: The integration may only have access to public channels by default

---

## Other Tools

If the user mentions a tool not covered above:
1. Check if it's available in Claude Desktop's integrations panel
2. If yes, guide them through the generic flow: Settings → Integrations → find it → Connect → authorize → verify
3. If not available as a first-party integration: "That tool isn't available as a direct integration yet. We can still work with it in other ways — for now let's note it in your tool stack and move on."

Don't let a missing tool block the onboarding flow.

---

## If They Don't Have Claude Desktop

If the user only has Claude Code (CLI) and not the Desktop app:

> "The easiest way to connect tools like Gmail and Calendar is through the Claude Desktop app. If you'd like to set that up:
> 1. Download it from claude.ai/download
> 2. Sign in with your Claude account
> 3. Connect your tools in Settings → Integrations
> 4. They'll automatically be available in Claude Code too
>
> If you'd rather skip this for now, that's totally fine — we can still build your workspace. The interview will just ask you a few more questions to learn about your writing style instead of pulling from your emails."

Don't pressure them. The onboarding works without tools — the discovery scan just has less to work with.
