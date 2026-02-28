# Setup Guide

**Getting Claude connected to your Figma files — step by step.**

This takes about 30 minutes the first time. After that, QA is a prompt away.

---

## What you're setting up

You're connecting two tools:

1. **Claude Desktop** — the desktop version of Claude AI (different from the browser version at claude.ai — this one supports file and tool connections)
2. **Figma MCP** — a bridge that lets Claude read your actual Figma file data: text, colors, fonts, spacing, components

Once connected, Claude has access to the real data inside your Figma files — not screenshots. That's what makes the QA thorough enough to actually be useful.

---

## Before you start

You'll need:

- **Figma desktop app** (not the browser version) — the MCP server runs through the desktop app
- **A Figma paid plan** — Dev Mode is required for the MCP, and Dev Mode requires a paid seat
- **A Claude account** — free tier works for getting started (claude.ai)

---

## Step 1: Download Claude Desktop

Claude Desktop is the version of Claude that supports MCP connections. The browser version (claude.ai) does not.

1. Go to **https://claude.ai/download**
2. Download and install the Mac or Windows app
3. Sign in with your Claude account (or create a free one)

---

## Step 2: Enable Dev Mode MCP in Figma

1. Open the **Figma desktop app** (not the browser)
2. Update to the latest version if prompted
3. Go to **Figma menu → Preferences** (Mac: Figma → Preferences, Windows: Edit → Preferences)
4. Find **"Dev Mode MCP Server"** and toggle it on
5. You'll see a confirmation that the local server is running at `http://127.0.0.1:3845/sse`

> **Don't see Dev Mode in Preferences?** You may need to enable Dev Mode on a specific file first. Open a Figma file, click the toggle in the top right to switch to Dev Mode view, then check Preferences again.

---

## Step 3: Connect Figma MCP to Claude Desktop

Claude Desktop is configured by editing a JSON file. This sounds technical but it's just opening a file and pasting in a few lines.

**On Mac:**

1. Open **Terminal** (search "Terminal" in Spotlight)
2. Type this command and press Enter:
   ```
   open ~/Library/Application\ Support/Claude/
   ```
3. You'll see a Finder window open. Look for a file called `claude_desktop_config.json`
   - If it doesn't exist, create a new file with that exact name
4. Open the file in a text editor (TextEdit works)
5. Replace the entire contents with:
   ```json
   {
     "mcpServers": {
       "figma": {
         "url": "http://127.0.0.1:3845/sse"
       }
     }
   }
   ```
6. Save the file

**On Windows:**

1. Press `Windows + R`, type `%APPDATA%\Claude\` and press Enter
2. Follow the same steps 3–6 above

---

## Step 4: Restart Claude Desktop

Fully quit Claude Desktop and reopen it. The MCP connection only loads on startup.

To verify it worked:
1. Open Claude Desktop
2. Look for a small **plug icon** or **tools icon** at the bottom of the chat input
3. Click it — you should see "figma" listed as a connected tool

If you don't see it, double-check that:
- The Figma desktop app is open and running
- Dev Mode MCP Server is toggled on in Preferences
- The config file was saved correctly (valid JSON — no missing commas or brackets)

---

## Step 5: Open your Figma file and run your first QA

1. Open the Figma file you want to review in the **Figma desktop app**
2. Switch to **Dev Mode** (toggle in top right)
3. Open **Claude Desktop**
4. Paste one of the prompts from the `/prompts` folder
5. Tell Claude which frame or page to review — use the exact frame name from your Figma file

Example:
> *"Review the frame called 'Homepage – Hero' for copy errors using the copy QA checklist."*

Claude will use the Figma MCP to pull the actual text, colors, and specs from that frame and run through the checklist.

---

## What Claude can access via the Figma MCP

| Data type | What Claude can verify |
|-----------|----------------------|
| Text content | Copy errors, typos, grammar, consistency |
| Color fills | Exact hex values — verify against brand guide |
| Typography | Font family, weight, size, line height |
| Component names | Whether correct components from the design system are used |
| Frame dimensions | Spec accuracy for print or digital |
| Spacing values | Padding, margins, gap values |
| Layer structure | Hierarchy, naming, organization |

---

## Giving Claude your brand guide

For color, typography, and brand consistency checks, paste the relevant sections of your brand guide into the conversation before running a QA prompt. Example:

> *"Here are our brand colors: Primary blue #1A3C8F, Secondary grey #6B7280, White #FFFFFF. Here are our approved fonts: Headlines — Canela Display Bold, Body — Inter Regular and Medium. Now review the 'Email Header' frame for brand compliance."*

Claude will then compare what it finds in Figma against what you've provided.

---

## Troubleshooting

**"Claude doesn't seem to have access to my Figma file."**
Make sure the Figma desktop app is open, Dev Mode is active on the file you want to review, and the MCP server toggle is on in Preferences. Claude can only see files that are open in Dev Mode.

**"I get a connection error in Claude."**
Restart both Figma desktop and Claude Desktop. The MCP server occasionally needs a fresh start.

**"My config file has an error."**
JSON is strict about formatting. Common mistakes: a trailing comma after the last item, or missing a closing bracket. Paste your config into https://jsonlint.com to check for errors.

**"I don't see Dev Mode in Figma."**
Dev Mode requires a paid Figma seat. If you're on the free plan, you won't have access to it.

---

## One-time setup. Permanent workflow improvement.

Once this is configured, it stays connected. Every time you open Figma desktop and Claude Desktop, the MCP is active. Running QA becomes: open file, open Claude, paste prompt, get results.
