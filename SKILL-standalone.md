---
name: is-there-a
description: "Is There A? — checks whether someone has already built what the user is about to build, before any building starts. Answers has someone built this, does this already exist, is my idea taken, what's out there for X, and prior art / existing products / competitor / market scan questions. Use whenever the user describes something they want to create, build, make, launch, design, prototype, or start — an app, tool, website, agent, script, extension, SaaS, physical product, brand, or service — even when they don't ask about competitors and even when they just want to start immediately. Trigger on the intent to build, not on the word competitor. Do not trigger for work inside an existing project, or for purely creative asks like naming, logos, sketches, copy, or campaign concepts. Skip if the user declines."
---

# Is There A? (single-file edition)

Self-contained version — everything needed is in this file, with no external references. Use this
when the skill is stored as a single file. The multi-file version at
`github.com/n-any-i/is-there-a` is identical in method.

## Why this exists

For almost any idea, someone has already built a version of it. That's not bad news — it's the
cheapest information available. It shows what's solved, what's hard, what people complain about,
and where the actual opening is.

The expensive mistake isn't building something that exists. It's spending three weeks rebuilding it
*without knowing*, and finding out when you show a friend.

Two things make this worth running automatically. The person who most needs the check is the one who
doesn't think to ask — and often wouldn't know how to phrase the search if they did. And agents are
tuned to execute: given "I want to build X", the default is to start building X. This inserts one
cheap step before that reflex.

## Posture: advisor, not gatekeeper

- Offer the scan, don't impose it. One line, then act on the answer.
- "This exists" is never by itself a reason to stop. Most good products are the fifth entrant.
- Never judge whether the idea is original. Report what's out there; let the user decide.
- If the user says "skip", "just build it", or shows impatience — drop it immediately and start
  building. Don't re-offer in that session.
- Don't refer the user to paid research products or "for deeper analysis, try X" services. If they
  want more, tell them what to search themselves.

## When to trigger

Trigger on **build intent** — the user is describing a thing they intend to make. Not just software:

- "a CLI that summarizes my git history into a weekly changelog"
- "an app where dog owners find sitters nearby"
- "a Chrome extension that strips tracking params from URLs"
- "a chewable coffee brand for people who don't have time to brew"
- "a car park panel that shows drivers where the free spaces are"
- "a service that helps elderly people digitize old photo albums"

**Do not trigger for:**

- Work inside an existing project — bug fixes, refactors, features in something already built
- Learning exercises where building it yourself is the point
- Internal one-off scripts with no product surface
- **Purely creative or executional asks** — naming, logos, sketches, mockups, copy, campaign
  concepts. "Design a logo for my coffee brand" is executing something already decided;
  "I want to start a coffee brand" is not.
- A scan already ran this session, or the user declined

The test: are they deciding **what to make**, or executing something already decided?

If the user is clearly in flow and just wants output, give them the output and offer the scan after.
Interrupting momentum has a real cost.

## The opening move

Ask once, briefly, with the cost visible:

> Before we build — want me to check what already exists?
> **Quick** (~2 min, ~50k tokens) or **Standard** (~10–15 min, ~200k tokens, written report).
> Quick is usually enough. Say skip and I'll go straight to building — and tell me if there's
> anything specific you want me to look for.

**Quick is the default.** If the user says yes without choosing, run Quick. Scanning is iterative: a
cheap scan tells you whether depth is warranted, and its results tell a deeper scan what to look
for. Don't offer a menu of options beyond this — it's friction at the moment they want to start.

If the user names something specific they want, fold it in as extra emphasis — but keep the standard
structure and don't let one request narrow the whole scan.

| Mode | Budget | Output |
|---|---|---|
| **Quick** (default) | 4–6 queries, 2–3 verifications, ~2 min | Chat summary, no file |
| **Standard** | 8–12 queries, 6–8 verifications, one complaint pass, ~10–15 min | Written report + summary |

---

## Step 1 — Write the scan spec before searching

Bad scans come from searching the user's product name instead of their problem. Compress the idea
into five lines and show the user so they can correct you:

```
IDEA:      one sentence, plain language
JOB:       the job the user's user is hiring this to do
WHO:       who specifically has this problem
MECHANISM: the how — technical, physical, or service approach
WEDGE:     the constraint or insight the user believes is their edge
```

The WEDGE matters most. "Todo app" is crowded; "todo app that reads your calendar and refuses to let
you overcommit" may not be. If the user hasn't articulated a wedge, say so — that's a finding worth
surfacing before anything gets built.

## Step 2 — Search across the naming gap

The biggest failure mode is searching one phrasing, finding nothing, and declaring the field empty.
Things that do the same job rarely use the same words. Write the queries as a batch across four
registers before running any:

1. **The user's words** — their phrasing, in case the category already has that name.
2. **The vendor's words** — how this appears on a pricing page, a package, or in trade press.
   "App that nags me about spending" → "budget alerts". "Chewy coffee thing" → "caffeinated chew",
   "functional confectionery".
3. **The sufferer's words** — how someone with the problem searches at 11pm:
   `"is there an app/product that" <problem>` · `"how do I" <problem> "without" <incumbent>` ·
   `<problem> reddit` · `"anyone know a" <thing>`
4. **The adjacent category** — the established thing this would be a variant or feature inside of:
   `<incumbent> <feature>` · `<incumbent> alternative` · `<category> for <specific user>`

**Useful modifiers:** `site:github.com` · `site:reddit.com` · `"Show HN"` · `"open source" <concept>`
· `<concept> alternative` · `<concept> "vs"` · `<concept> kickstarter` · `<concept> patent`

### Surfaces by product type

Search general web plus two to four surfaces matching what's being made.

| Type | Where to look |
|---|---|
| SaaS / web app | Product Hunt, G2, Capterra, AlternativeTo, Y Combinator directory, IndieHackers |
| Dev tool / library / CLI | GitHub (search + topics), npm, PyPI, crates.io, Homebrew, awesome-* lists, "Show HN" |
| Browser extension | Chrome Web Store, Firefox Add-ons, Edge Add-ons, GitHub |
| AI agent / skill | GitHub topics, MCP and skill directories, agent marketplaces, Hugging Face Spaces |
| Mobile app | App Store, Google Play — search the *problem phrase*, not brands |
| Platform add-on | that platform's own marketplace, first (Slack, Notion, Shopify, VS Code, Figma…) |
| Food / drink / CPG | Amazon (read the 1-star reviews), specialist retailers, Kickstarter, trade press, Instagram/TikTok brand search, retail category pages |
| Hardware / device | Alibaba and Made-in-China (the commodity version), Amazon, Kickstarter, trade show exhibitor lists, patents |
| Industrial / civic systems | find the trade term first, then vendor directories, tender records, case studies, industry associations |
| Service business | Google Maps in three different cities, category directories, franchise directories, local communities |
| Marketplace / two-sided | search each side separately — the real incumbent is often a Facebook group |
| Consumer / community | Reddit (subreddit wikis list every tool), Discord, niche forums |

Run one GitHub pass even for non-software ideas — hobbyist and research versions rarely have
marketing pages.

### Two rules that keep results honest

- **Empty results mean bad queries until proven otherwise.** Before writing "no direct competitors",
  run at least two more registers and one different surface. Truly empty categories exist but are
  rare, and falsely claiming one is the worst thing this skill can do.
- **Verify before listing.** Open the page, listing, or repo. Never list something from a search
  snippet alone — abandoned projects, renamed products and AI-generated listicles all look real in
  snippets. Note last commit, last release, or "last updated" where visible.

### Is it alive?

| Signal | Alive | Dead / stale |
|---|---|---|
| Last commit or release | < 6 months | > 18 months |
| Changelog, blog, social | posts this year | last post 2+ years ago |
| Pricing or product page | loads, current | 404 or "contact us" only |
| Store listing | updated this year | "last updated" 3 years ago |
| Stock (physical) | in stock | permanently out of stock |

Label each entry **active**, **maintenance**, or **dormant**. A dormant product with users is an
opportunity, not a competitor.

### If you have no web access

Run it from model knowledge, but: label the whole report unverified at the top; mark confidence per
entry (high / medium / low); say nothing about pricing, funding or current status; state the
knowledge cutoff; and end with the exact queries and surfaces the user should check themselves. A
fabricated competitor is worse than an admitted blind spot — the user might abandon a good idea over
a product that doesn't exist. The scan spec, the four vocabularies, the category structure and the
workaround analysis all still work offline, and are often the most valuable parts.

## Step 3 — Sort into four named groups

Use these names, not numbers — numbered tiers leave a visible hole when one is absent, and a hole
reads as lost data.

- **Direct hits** — same job, same user, comparable mechanism
- **Adjacent** — same job/different user, or same mechanism/different job. Where most
  differentiation ideas come from
- **Components** — libraries, APIs, services, suppliers, manufacturers solving *part* of it
- **Graveyard** — abandoned repos, shutdowns, discontinued products, funded-but-never-shipped
  crowdfunding. The most underrated group: it tells you the failure mode, and sometimes tells you
  the enabling conditions have since changed. In some categories the graveyard is
  published-but-never-adopted — near-zero stars, downloads or reviews is the same signal

**Every group gets a status line, always:** `3 found`, `None found`, or `Not searched at this
depth`. A report that quietly omits what it didn't check undermines the one thing this skill sells.
Never let the reader guess which kind of absence they're looking at.

## Step 4 — Map the overlap honestly

For each capability in the idea, mark **already solved** (name who), **partial** (name the
limitation), or **open**. Be specific — "Notion AI summarizes pages but can't act on external tools"
is useful; "Notion is similar" is not.

## Step 5 — Find gaps from evidence, not imagination

Gaps must trace to something actually read:

- 1–3 star reviews and support threads on the direct hits — what people churn over
- Open issues or feature requests with many reactions, especially long-unanswered ones
- Threads where someone asks for exactly this and gets unsatisfying answers
- Pricing — who is priced out, what's gated behind the top tier
- Coverage gaps — a platform, region, language, segment, or compliance regime

Cite where each gap came from. Anything inferred goes in a separate **Hypotheses** list, clearly
labeled. An imagined gap is worse than no gap, because it reads as validation.

**The real incumbent is often not a product.** Before concluding a space is empty, ask what people
do today without any tool — a group chat, a spreadsheet, an Instagram account, a paper sign by the
door. That workaround is free, already adopted, and where the users already are. Plugging into it
usually beats replacing it; asking people to adopt a new destination is the most common way these
ideas quietly fail.

## Step 6 — Differentiation directions, then a verdict

Offer 3–5 directions phrased as **positions**, not features — "the local-first one for data that
can't leave the building", "the one that posts into the group chat people already use", "free for
the 90% case, paid for teams". For each, name the evidence and roughly what it costs.

Note where distribution sits. For most ideas at this scale, getting found is harder than getting
built — so if you noticed how existing players got their users (a directory, a marketplace, a
community, a retailer, being a feature inside something bigger), say so.

Then land on **one** verdict:

- **Build it** — real gap with evidence, or incumbents that are dormant, mispriced or badly rated.
  Say what to build first: the smallest thing that tests the wedge.
- **Build it narrower** — the general version is taken; a specific slice isn't. The most common good
  outcome. Name the slice concretely.
- **Wrap it** — something existing does the hard part; the value is the layer on top.
- **Fork or extend it** — an open project is most of the way there and the licence permits it. Check
  the maintainer's responsiveness; contributing upstream is often faster and inherits the users.
- **Use what exists** — it genuinely already exists and works, below the cost of the user's time.
  Say it once, plainly, naming the thing. Then respect their answer if they still want to build.
- **Reframe it** — the graveyard suggests this framing fails; here's the adjacent one.

**Rules that keep the verdict honest.** One verdict, not three — hedging is not advice; note the
runner-up in a line. Show two or three specific findings as evidence. Calibrate confidence (high /
medium / low) and say why. Never grade the idea. And always attach **"what would change my mind"** —
the thing the user knows that you don't which would flip it. Their context usually beats the scan's.

**Bias check before delivering.** Did a pile of Adjacent results make this feel more crowded than the
Direct hit count justifies? Was anything listed from a snippet without opening it? Is every gap
traceable to something read? Did you look for the workaround incumbent? Would the verdict change if
the user already has an audience?

## Step 7 — Deliver, then hand the conversation back

**Quick:** summarize in chat. No file unless asked.

**Standard:** write `LANDSCAPE.md` in the project directory (or `docs/`), dated, listing which
surfaces were searched *and which weren't*. Then give a short chat summary — closest existing thing,
sharpest gap, verdict — and don't restate the report.

Report structure:

```markdown
# Landscape: <idea in five words>

**Scanned:** <date> · **Mode:** standard
**Searched:** <surfaces> · **Not searched:** <surfaces skipped, and why>
**Confidence:** high / medium / low — <why>

## The idea
<table: idea / job / who / mechanism / wedge>

## Verdict
**<one verdict>** — <2-4 sentences pointing at findings below>
**Runner-up:** … · **What would change this:** …

## Direct hits
*<N found / None found / Not searched at this depth>*
| Product | What it is | Status | Overlap | Where it stops |

## Adjacent
*<status line>*
| Product | Why it's adjacent | What to learn from it |

## Components
*<status line>*
| Thing | Covers | Saves |

## Graveyard
*<status line>*
| Attempt | When | Apparent failure mode | Has anything changed? |

## What people do today without any product
<the workaround — the real incumbent>

## Overlap map
| Capability | already solved / partial / open | Who does it | Notes |

## Gaps found (with evidence)
1. **<Gap>** — <what's missing> · *Evidence:* <quote or link>
### Hypotheses (unverified)

## How the existing players get found
<distribution, 1-2 sentences>

## Differentiation directions
1. **<Position, not a feature>** — <meaning> · *Evidence:* … · *Cost:* …

## What to build first
## Open questions for you
```

Link every entry — an entry without a URL can't be checked, and unlinked entries are where invented
ones hide. "Where it stops" is the most valuable column: it's the seam between what exists and what
the user could build.

Then **offer next steps as questions, and wait.** Don't generate specs, briefs or dashboards
unasked — the point is to hand the user back the wheel with better information, not to produce more
documents. Pick two or three that fit what actually happened:

- "I skipped [surfaces] on this run — want me to check them?"
- "Want to brainstorm what to build, given what turned up?"
- "Want to dig into any of these competitors properly?"
- "Want me to write this up as a handoff note, so you can start a fresh chat with it?"
- "Do you need to show this to someone? I can prepare it for that."
- "Ready to build? I'd start with [smallest thing that tests the wedge]."

If the user just wants to build, build. The scan serves the build; it isn't the deliverable.

## What this costs and how it loads

Worth explaining plainly if the user asks:

- Only the name and description sit in context permanently — roughly 200 tokens. That's the entire
  cost of having this installed in a session where it never fires.
- These instructions load only when the skill triggers.
- The scan itself is the real cost: ~50k tokens for Quick, ~150–300k for Standard. That's why the
  mode is offered with numbers attached rather than chosen silently.

## Failure modes to avoid

- **Listicle laundering.** "Top 10 tools for X" pages are affiliate SEO, often listing dead or
  irrelevant products. Use them for candidate names, never as evidence.
- **Big-name padding.** Listing Google, Amazon or Notion as competitors to a niche idea is noise.
- **Silent omission.** Never present a group as absent when it was merely unsearched.
- **Scan sprawl.** Twenty minutes into a Standard scan, stop and deliver.
- **Discouragement by volume.** A long competitor list reads as "don't bother" even when it isn't.
  Lead with the gap and the verdict, not the count.
- **Stale-as-live.** Untouched for three years is graveyard, not competition. Label it.
- **Referral drift.** Don't point users at paid research tools. Give them the queries.
