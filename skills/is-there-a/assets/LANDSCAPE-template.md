# Landscape Report Template

For Standard scans. Copy this structure into `LANDSCAPE.md`.

The one rule that overrides brevity: **every group keeps its heading and gets a status line**, even
when empty. A reader must never have to guess whether a group is missing because nothing was found
or because nothing was searched. Everything else can be trimmed.

Keep the whole report under about four screens.

---

```markdown
# Landscape: <idea in five words or fewer>

**Scanned:** <YYYY-MM-DD> · **Mode:** standard
**Searched:** <e.g. general web, GitHub, Product Hunt, Amazon, Reddit>
**Not searched:** <the surfaces skipped, and why — budget, not applicable, no access>
**Confidence:** high / medium / low — <one line on why>

## The idea

| | |
|---|---|
| **Idea** | <one sentence> |
| **Job** | <the job it's hired to do> |
| **Who** | <the specific user> |
| **Mechanism** | <the how> |
| **Wedge** | <the claimed edge — or "not yet articulated"> |

## Verdict

**<Build it / Build it narrower / Wrap it / Fork it / Use what exists / Reframe it>**

<Two to four sentences of reasoning, pointing at specific findings below.>

**Runner-up:** <one line>
**What would change this:** <the user-held fact that would flip the verdict>

## Direct hits

*<N found / None found / Not searched at this depth>*

| Product | What it is | Status | Overlap | Where it stops |
|---|---|---|---|---|
| [Name](url) | <one line> | active / maintenance / dormant | high / partial | <the limitation> |

## Adjacent

*<N found / None found / Not searched at this depth>*

| Product | Why it's adjacent | What to learn from it |
|---|---|---|
| [Name](url) | <same job, different user — or vice versa> | <the borrowable idea> |

## Components

*<N found / None found / Not searched at this depth>*

| Thing | Covers | Saves |
|---|---|---|
| [Name](url) | <the part of the idea it handles> | <rough effort saved> |

## Graveyard

*<N found / None found / Not searched at this depth>*

| Attempt | When | Apparent failure mode | Has anything changed? |
|---|---|---|---|
| [Name](url) | <year> | <why it stalled> | <yes/no + what> |

> Also note published-but-never-adopted entries here — near-zero stars, downloads, reviews, or
> followers is the same signal in a different form.

## What people do today without any product

<The workaround: the group chat, the spreadsheet, the Instagram account, the paper sign. Name it —
it's the real incumbent, and integrating with it often beats replacing it.>

## Overlap map

| Capability in the idea | Status | Who does it | Notes |
|---|---|---|---|
| <capability> | already solved / partial / open | <product> | <detail> |

## Gaps found (with evidence)

1. **<Gap>** — <what's missing> · *Evidence:* <quote or link>
2. **<Gap>** — <what's missing> · *Evidence:* <quote or link>

### Hypotheses (unverified)

- <anything inferred rather than read — kept separate on purpose>

## How the existing players get found

<One or two sentences: directories, marketplaces, launch platforms, communities, retail, being a
feature inside something bigger, institutional buyers. For ideas at this scale, distribution is
usually the harder half.>

## Differentiation directions

1. **<Position, not a feature>** — <what it means> · *Evidence:* <why> · *Cost:* <what it takes>
2. **<Position>** — …
3. **<Position>** — …

## What to build first

<The smallest thing that tests the wedge — 2–5 concrete bullets.>

## Open questions for you

1. <question whose answer would sharpen the verdict>
2. <question>

---
*Scans go stale. Re-run before any significant investment of time or money.*
```

---

## Notes on filling this in

- **Link everything.** An entry without a URL can't be checked, and unlinked entries are where
  invented ones hide.
- **"Where it stops" is the most valuable column.** It's the seam between what exists and what the
  user could build. Be specific: a named missing capability, a platform, a price point, a workflow.
- **Keep each group to three to six entries.** Completeness isn't the goal; a clear map is.
- **Hypotheses stay separate from gaps.** Mixing them makes the whole report less trustworthy.
- **Date it and name the surfaces, including the ones you skipped.** Six weeks later the reader
  needs to know what this covered and what it never looked at.
- **Don't generate a spec, brief, or dashboard off the back of this.** Offer, and wait to be asked.
