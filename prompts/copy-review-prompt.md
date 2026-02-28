# Copy Review Prompt (Figma MCP)

**How to use:**
1. Make sure the Figma desktop app is open with your file in Dev Mode
2. Open Claude Desktop (MCP must be connected — see SETUP.md)
3. Paste this entire prompt into a new conversation
4. Replace `[FRAME NAME OR URL]` with your actual frame name or Figma frame URL
5. Optionally paste your brand voice guidelines at the bottom

---

I need you to perform a thorough copy QA on a Figma frame.

**Step 1:** Use the Figma MCP to access the frame called `[FRAME NAME OR URL]` and extract all text content from it. Pull every text layer — headlines, body copy, labels, CTAs, footnotes, legal copy, everything. List what you find before beginning the review so I can confirm you've captured everything.

**Step 2:** With that text content, check for each of the following. For every issue found, note the exact text, the problem, and a suggested fix.

**Spelling & Typos**
Flag every misspelled word. Be especially careful with proper names, location names, program names, and branded terms. Check these against any brand guidelines I've provided.

**Grammar**
Check for: comma usage, apostrophe errors, incorrect punctuation, capitalization errors, incorrect verb tense, run-on sentences, sentence fragments, and duplicated words.

**Punctuation Rules**
- No comma before an ampersand (e.g. "sales, marketing & design" not "sales, marketing, & design")
- Identify Oxford comma usage — flag any inconsistencies within this file
- Slash spacing: short phrases use no spaces (his/her), longer phrases may use spaces — flag inconsistencies
- En-dash and em-dash: identify which is used and flag inconsistent usage or spacing
- 401(k) must be written exactly that way — not 401K
- Thousands abbreviation: lowercase k only (e.g. $25k not $25K)

**Headline Capitalization**
Identify the capitalization style in use (title case, sentence case, or all caps). Flag any headlines or subheads that don't match the established style.

**Voice & Clarity**
- Flag passive voice and suggest active alternatives
- Flag any placeholder text remaining (Lorem Ipsum, [INSERT TEXT], TBD, etc.)
- Flag any CTAs that are vague or don't clearly indicate what happens when clicked

**Quotes**
If there are any pull quotes or testimonials: check they are complete sentences and in present tense. Flag fragments or past-tense quotes.

**Widows & Orphans in Copy**
Based on the text content, flag any instances where a single short word would likely appear alone on the last line of a text block. Note that visual confirmation requires looking at the actual frame, but flag copy that commonly causes this issue.

**Step 3:** Provide a summary at the end:
- Overall copy health (one sentence)
- Total number of issues found, broken down by category
- Any patterns worth noting (e.g. "em-dash usage is inconsistent throughout" or "CTAs are consistently vague")

---

Format each issue as:
> **[Category]** | Original: *"exact text"* | Problem: what's wrong | Fix: suggested correction

If a category has no issues, note: ✅ Clean

---

**Brand voice guidelines (paste here if applicable):**
[PASTE YOUR BRAND VOICE GUIDE OR TONE NOTES HERE — OR DELETE THIS LINE]
