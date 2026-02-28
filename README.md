# Figma QA Toolkit

**A quality assurance system for graphic designers working in Figma — powered by Claude AI and the Figma MCP.**

---

## Why this exists

My fiancée is a graphic designer. She told me design QA is a pain — verifying every color code, font, spacing value, and copy error before anything goes to a client takes forever and it's not the interesting part of the job.

So I built this. It connects Claude to your Figma files directly so it can check actual file data — not screenshots. Screenshots don't tell you if a hex value is wrong. The Figma MCP does.

Not a designer. Sharing it anyway.

---

## What's required

- **Figma** (desktop app, paid plan — Dev Mode is required for MCP)
- **Claude Desktop** (free download) with the Figma MCP connected
- About 30 minutes to set up — once. Then it's part of your workflow.

Setup guide: [`SETUP.md`](SETUP.md)

---

## What's in here

| File | What it does |
|------|-------------|
| `SETUP.md` | Full Figma MCP setup — step by step, no technical background assumed |
| `checklists/copy-qa.md` | Line-by-line copy review checklist |
| `checklists/design-qa.md` | Full design QA — typography, layout, brand, photography |
| `checklists/creative-director-review.md` | Strategic review — brief alignment, client experience, creative standards |
| `checklists/final-handoff.md` | Pre-delivery checklist — files, exports, links, naming |
| `prompts/copy-review-prompt.md` | Claude prompt for copy QA via Figma MCP |
| `prompts/design-spec-prompt.md` | Claude prompt to pull and verify design specs from Figma |
| `prompts/component-audit-prompt.md` | Claude prompt to audit component consistency across a file |
| `prompts/brief-analysis-prompt.md` | Claude prompt to analyze a brief before starting a project |

---

## How it works

**Claude connects directly to your Figma file** via the Figma MCP (Model Context Protocol). This means:

- Claude reads the actual text content of your frames — not a screenshot of it
- Claude pulls exact hex color values — not an interpretation of what the color looks like
- Claude sees font family, weight, size, and line height — not a guess based on visuals
- Claude reads component names — so it can tell you if something is the right component or a manual recreation

**You run the prompts inside Claude Desktop** with your Figma file connected. Claude uses the Figma MCP tools to pull the data, then runs through the checklist systematically and flags everything that needs attention.

**The checklists tell you what needs human judgment.** Not everything can be automated — creative decisions, brand feel, whether something *works* — those are marked clearly so you know what needs your eye.

---

## What this is not

This is not a tool that designs for you or replaces design judgment. It's a QA layer that catches spec errors, copy mistakes, and consistency issues before a client does — the meticulous checking work that's important but doesn't require creative talent to execute.

The design is entirely yours. Claude is checking the math.

---

## A note on AI and design

There's a real conversation happening about AI and design jobs. This toolkit isn't part of that debate. It's a spell-checker for design files — except instead of just catching typos, it catches wrong hex values, mismatched fonts, and broken component usage.

---

## Contributing

Found something missing? A prompt that works better? Open a PR or file an issue.

---

*Built by a non-designer, for a designer. Figma-specific, MCP-powered, actually useful.*
