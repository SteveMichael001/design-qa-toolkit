# Design Spec Verification Prompt (Figma MCP)

**How to use:**
1. Figma desktop app open, file in Dev Mode, Claude Desktop connected
2. Have your brand guide or approved spec sheet ready to paste in below
3. Replace `[FRAME NAME OR URL]` with the actual frame name or URL
4. Paste brand colors, fonts, and spacing system into the marked sections below

This prompt pulls actual values from your Figma file and compares them against your brand specs. This is not a visual review — it's a data verification pass.

---

I need you to perform a design spec QA on a Figma frame. Use the Figma MCP to access the frame and pull the actual data — not a visual description of it.

**Frame to review:** `[FRAME NAME OR URL]`

---

**Step 1: Pull and report the raw data**

Before any analysis, use the Figma MCP to extract and list the following from the specified frame:

- **All color fills used** — list every unique hex value found in the frame, and which element it's applied to
- **All fonts used** — list every unique combination of font family, weight, and size found, and where each is used
- **Frame dimensions** — the exact width and height of the frame
- **Spacing values** — list any padding, margin, or gap values you can access on the major layout containers
- **Component names** — list any Figma components used in this frame and their full component names

Present this as a data table before proceeding to the analysis.

---

**Step 2: Verify against brand specifications**

Compare what you found against the specs I've provided below. Flag every discrepancy — no matter how small.

**Color check:**
For each color found in Step 1, check if it matches an approved brand color. Flag any color that is:
- Not in the approved palette
- Close to an approved color but not an exact match (e.g. `#1A3D8F` when the approved value is `#1A3C8F`)
- Used in a context that doesn't match the brand guide (e.g. primary color used as a background when it's only approved for text)

**Typography check:**
For each font combination found in Step 1, check against approved typography. Flag:
- Any unapproved font family
- Any unapproved weight for a given family
- Any size that falls outside the approved type scale
- Inconsistent use of the same text role (e.g. two different sizes used for body copy)

**Spacing check:**
Where spacing data is available, flag values that don't align with the spacing system provided. Note any areas where spacing data wasn't accessible via MCP (some spacing may require manual verification).

**Component check:**
For each component found in Step 1, flag:
- Any component name that doesn't match the approved design system
- Any element that appears to be a manually recreated version of a component rather than an instance of it

**Frame dimensions check:**
Confirm the frame dimensions match the required spec for this deliverable type.

---

**Step 3: Summary**

Provide:
- Overall spec compliance rating (Clean / Minor issues / Significant issues)
- A prioritized list of issues: Critical first (brand colors wrong, unapproved fonts), then Minor (spacing inconsistencies, naming)
- Anything that couldn't be verified via MCP and requires manual visual review

---

## Brand Specifications

**Paste your brand specs here before running. The more specific, the better.**

**Approved colors:**
```
Primary: #[HEX] — used for [context]
Secondary: #[HEX] — used for [context]
[Add all brand colors]
```

**Approved typography:**
```
Headlines: [Font Family] [Weight] — sizes: [size scale]
Body: [Font Family] [Weight] — sizes: [size scale]
Labels/Captions: [Font Family] [Weight] — sizes: [size scale]
```

**Spacing system:**
```
Base unit: [px]
Approved values: [4, 8, 16, 24, 32, 48, 64, etc.]
```

**Frame dimensions for this deliverable:**
```
Width: [px or inches]
Height: [px or inches]
Color mode: [RGB / CMYK]
Resolution: [72ppi / 300ppi]
```

**Design system / component library name:**
```
[Name of your component library in Figma]
```
