# Connecting Your Design Tools to AI

**Skip uploading files every time. Connect your tools directly.**

This guide covers how to give Claude (or other AI tools) direct access to your design files — so instead of exporting screenshots and uploading them manually, you can say "review the frame called Homepage Hero in my Figma file" and the AI looks at it directly.

This is optional. The prompts in this toolkit work perfectly well without any of these integrations. But if you're doing QA regularly, a direct connection saves real time.

---

## Honest complexity ratings

Before anything else: these integrations vary in difficulty. We're using a simple scale:

| Rating | What it means |
|--------|--------------|
| 🟢 Approachable | A motivated non-developer can do this in 30 minutes |
| 🟡 Moderate | Requires some comfort with config files or terminal commands |
| 🔴 Technical | Involves installing software, plugins, and running local servers — ask a developer friend |

---

## Figma → Claude

**Status:** ✅ Official integration — built and maintained by Figma

**What it does:** Gives Claude read access to your Figma files — design context, variables, components, layout data, and frame content — without you needing to export or share a file. Claude can review a specific frame, check component usage, or pull copy directly from a design.

**Complexity:** 🟡 Moderate

**Two ways to set it up:**

### Option 1: Local MCP (Figma Desktop App)

Best for: Designers already using the Figma desktop app

1. Open Figma desktop app
2. Go to **Preferences → Enable Dev Mode MCP Server**
3. The server runs locally at `http://127.0.0.1:3845/sse`
4. Connect it to Claude Desktop by editing your Claude config file (see below)

### Option 2: Remote MCP (No Desktop App Required)

Best for: Designers who work in the browser version of Figma

If you're using Claude Code or a terminal-based AI tool:
```
claude mcp add --transport http figma https://mcp.figma.com/mcp
```

If you're using Claude Desktop, add this to your Claude Desktop config file (`claude_desktop_config.json`):
```json
{
  "mcpServers": {
    "figma": {
      "command": "npx",
      "args": ["-y", "figma-developer-mcp", "--figma-api-key", "YOUR_FIGMA_API_KEY"]
    }
  }
}
```

Get your Figma API key: Figma → Settings → Security → Personal Access Tokens → Generate a token.

**What you can do once connected:**
- Ask Claude to review a specific frame by name or URL
- Have Claude pull copy directly from the design for copy QA
- Ask Claude to check component consistency across frames
- Reference live design context without exporting anything

**What you can't do (currently):** The official Figma MCP is read-only. Claude can see and analyze your designs but cannot edit them directly. Some community-built alternatives exist that add write access, but they're not officially supported.

**Figma's official documentation:** https://help.figma.com/hc/en-us/articles/32132100833559

---

## Adobe Creative Suite → Claude

**Status:** ⚠️ No official Adobe MCP for Photoshop, Illustrator, or InDesign — community-built options exist

**The honest picture:** Adobe has an extensive API and has added AI features aggressively (Firefly, Sensei, etc.), but as of early 2026, Adobe has not released an official MCP server for Creative Cloud desktop apps. This is surprising given the pace of MCP adoption industry-wide, and it may change — but don't assume it exists just because Adobe is a large software company.

What does exist:

### Community Option 1: adobe-mcp (GitHub)
**Complexity:** 🔴 Technical

A community-built MCP server that supports Photoshop, Premiere Pro, Illustrator, and InDesign. Requires:
1. Installing an Adobe plugin into each app
2. Running a local proxy server on your machine
3. Configuring Claude Desktop to connect to it

If you're comfortable with that setup, the GitHub repo is at:
`https://github.com/matrayu/adobe-mcp`

Not recommended as a first step if you're new to this. Get comfortable with Figma MCP first.

### Community Option 2: Creative Cloud Libraries via Zapier
**Complexity:** 🟢 Approachable (for Libraries specifically)

Zapier has a built-in connector for Adobe Creative Cloud Libraries. This doesn't give Claude access to open Photoshop or Illustrator files, but it does let Claude interact with your CC Libraries — assets, colors, fonts, and components you've saved there.

If your QA workflow involves checking brand assets (correct logo versions, color swatches, approved fonts), this is the most practical Adobe integration available right now without technical setup.

Setup: https://zapier.com/mcp/creative-cloud-libraries

### What about Adobe Express?
Adobe Express has an official developer MCP server, but it's designed for developers building Add-ons for Express — not for designers doing QA work on their files. Not relevant to this toolkit.

---

## The practical recommendation

**Start with Figma if you use Figma.** The integration is official, maintained, and genuinely useful for QA — especially pulling copy directly from frames for copy review, or checking component consistency without exporting anything.

**For Adobe CC:** The honest answer is that the tooling isn't as mature yet. The best current workflow is still the manual one — export a PDF or screenshot, upload it to Claude. For brand asset checks, the CC Libraries → Zapier path is worth exploring.

**Check back on Adobe.** This space is moving fast. Adobe will almost certainly have official MCP support for Creative Cloud apps at some point. When they do, it'll be worth a full setup.

---

## Claude Desktop vs. Claude.ai vs. Claude Code

Quick clarification on which Claude to use:

| Tool | What it is | MCP support | Best for |
|------|-----------|-------------|----------|
| **Claude.ai** | Browser-based chat at claude.ai | ❌ No MCP | File uploads, quick prompts |
| **Claude Desktop** | Desktop app (Mac/Windows) | ✅ Yes | MCP integrations, longer sessions |
| **Claude Code** | Developer CLI tool | ✅ Yes | Technical users, Figma remote MCP |

**For most designers:** Claude Desktop is the right tool for platform integrations. Download at: https://claude.ai/download

---

## A note on API keys and security

When connecting any tool to Claude, you'll generate an API key (a long string of letters and numbers). A few rules:

- Never share your API key with anyone
- Never paste it into a public document, GitHub repo, or Slack message
- Store it somewhere secure — a password manager works well
- If you think a key has been exposed, revoke it immediately in the platform's settings and generate a new one

These keys give access to your account and files. Treat them like a password.
