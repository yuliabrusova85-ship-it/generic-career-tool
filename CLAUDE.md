# AI Career Tools Workshop (Generic) — CLAUDE.md

## Project overview

Single-file HTML workshop simulator for students at any institution. Teaches responsible AI use in job searching: resume gap analysis, STAR method interview prep, LinkedIn profile scoring. No branding, no backend, no build step.

**File:** `ai-career-tools.html` (everything lives here)

---

## Stack

- Vanilla HTML/CSS/JavaScript — no framework, no build step
- **Chart.js** (CDN) — bar chart for resume competency visualization
- `localStorage` — all data persisted under `career_` prefix
- Font: `'Helvetica Neue', Arial, sans-serif` — neutral system font

---

## Key data structures (top of `<script>`)

| Structure | Shape |
|---|---|
| `FRAMEWORKS` | `{ nace: { name, competencies[] }, core10: { name, competencies[] } }` |
| `FRAMEWORKS[fw].competencies[]` | `{ name, keywords[], suggestion, verbs[] }` |
| `QUESTIONS` | `string[]` — 15 behavioral interview questions |
| `LI_SECTIONS` | `{ title, items[] }[]` — 5 sections, 20 checkboxes total |

---

## localStorage keys (all prefixed `career_`)

| Key | Value |
|---|---|
| `resume_text` | pasted resume string |
| `resume_fw` | selected framework (`nace` \| `core10`) |
| `active_tab` | last active tab (`resume` \| `interview` \| `linkedin`) |
| `star_{index}` | `{s,t,a,r}` object per question index (0–14) |
| `last_q` | last selected question index |
| `li_checks` | `{li_0: bool, li_1: bool, ...}` for all 20 checkboxes |

---

## Color tokens

| Token | Hex | Usage |
|---|---|---|
| `--primary` | `#2563EB` | Header bg, tab active border, buttons, STAR badges, score number |
| `--primary-dark` | `#1D4ED8` | Button hover, chart bar border |
| `--primary-lt` | `#DBEAFE` | (available for use) |
| `--black` | `#1E293B` | Nav bar, footer, secondary button |
| `--green` | `#16A34A` | Found competency, strong LinkedIn score |
| `--amber` | `#D97706` | Good-start LinkedIn score |

Tips box background: `#EFF6FF`. Chart bars: `#2563EB` (found) / `#D0D0D0` (missing).

---

## Score thresholds

**Resume:** ≤40% = Needs Development, ≤70% = Good Foundation, else Strong
**LinkedIn:** ≤50% = Needs Attention, ≤75% = Good Start, else Strong Profile

---

## Common tasks

**Add a new interview question:**
Append to the `QUESTIONS` array. No other changes needed.

**Add a LinkedIn checklist item:**
Add the string to the correct `items[]` array inside `LI_SECTIONS`. The total item count drives the score denominator — updates automatically.

**Add a new competency framework:**
1. Add a new key to `FRAMEWORKS` with the same shape as `nace`
2. Add an `<option value="newkey">` to `#framework-select`

**Change keyword matching logic:**
See `makeVariants()` and `matchKeywords()`. Currently generates stemmed variants and tests with `\bword\b` regex, case-insensitive.

**Retheme for an institution:**
Update `--primary` and `--primary-dark` in `:root`. The chart bar colors (`#2563EB`, `#1D4ED8`) are hardcoded in `renderResumeChart()` — update those too.

---

## Relationship to UofL version

This is a stripped, rebrandable version of the University of Louisville Libraries workshop tool. Key differences from the original:
- No "University of Louisville Libraries" header brand or footer credit
- Cardinal Red `#AD0000` → neutral blue `#2563EB`
- localStorage prefix `uofl_` → `career_`
- Export filename `uofl-career-workshop-export.txt` → `career-workshop-export.txt`
- STAR download and export headers have no institutional reference
