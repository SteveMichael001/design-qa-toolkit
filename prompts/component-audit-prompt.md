# Component Consistency Audit Prompt (Figma MCP)

**How to use:**
1. Figma desktop app open, file in Dev Mode, Claude Desktop connected
2. Use this when auditing an entire page or multiple frames — not just one
3. Replace `[PAGE NAME]` with the Figma page you want to audit
4. Provide your design system library name below

This prompt audits component usage across a page or file to catch inconsistencies before handoff — manually recreated components, mismatched instances, detached components, and naming drift.

---

I need you to audit component consistency across a Figma page. Use the Figma MCP to access the page and pull component data from all frames on it.

**Page to audit:** `[PAGE NAME]`
**Design system / component library:** `[YOUR LIBRARY NAME]`

---

**Step 1: Inventory all components**

Use the Figma MCP to extract every component instance used across this page. List:
- Component name
- How many times it appears
- Which frames it appears in

Present this as a table.

---

**Step 2: Flag inconsistencies**

With the component inventory, identify:

**Detached or manually recreated components**
Flag any element that appears to be a manually built version of a component rather than a live instance from the design system. Signs include: elements that visually match a component but don't carry a component name, or component names that don't match the library.

**Mismatched variants**
Flag cases where the same UI element (e.g. a button, a card, a badge) appears in multiple frames using different component variants when they should be consistent.

**Naming drift**
Flag any component names that don't match the library naming convention — e.g. a button named "Button/Blue" in one frame and "CTA Button" in another that appear to be the same component.

**Outdated instances**
If you can detect whether component instances are linked to the current library version or appear to be out of date, flag them.

**Missing components**
Based on the UI patterns visible in the page, flag any elements that should be components (buttons, form fields, navigation items, icons) but don't appear to be component instances.

---

**Step 3: Spacing and alignment consistency**

Across the frames on this page, flag:
- Inconsistent use of the same element type at different sizes (e.g. headlines at different sizes across similar frames)
- Padding inconsistencies within the same frame type (e.g. card components with different internal padding across different frames)

---

**Step 4: Summary**

Provide:
- Total number of component instances found
- Number and list of inconsistencies flagged
- Top 3 priorities to fix before handoff
- Anything that requires manual visual verification beyond what MCP data can confirm
