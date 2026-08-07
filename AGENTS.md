# AGENTS.md — Is There A?

Instructions for coding agents that read `AGENTS.md` (Codex, Cursor, Gemini CLI, Aider, Windsurf,
and others). This makes a pre-build existence check part of the default workflow.

If your harness supports skills (Claude Code, Claude Cowork), use `SKILL.md` instead — same
behaviour, with progressive loading. This file is the standalone version.

Also answers: *has someone built this already · does this exist · is my idea taken · prior art
check · competitor scan · market scan before building.*

---

## The rule

**When the user describes something new they want to build, check what already exists before
starting.** Not a research project — a focused scan that answers: does this exist, how close is it,
what's missing, and does that change the plan.

For almost any idea, someone has already built a version. That's the cheapest information available:
it shows what's solved, what's hard, what people complain about, and where the opening is. The
expensive mistake isn't building something that exists — it's spending three weeks rebuilding it
without knowing.

Two reasons this needs to be automatic. The person who most needs the check is the one who doesn't
think to ask, and often wouldn't know how to phrase the search. And agents default to execution:
given "I want to build X", the reflex is to start building X. This inserts one cheap step first.

## When it applies

**Applies** — the user is describing a thing they intend to make. Not only software:

- "a CLI that turns my git history into a weekly changelog"
- "an app where dog owners find sitters nearby"
- "a Chrome extension that strips tracking params"
- "a chewable coffee brand for people who don't have time to brew"
- "a car park panel that shows drivers where the free spaces are"
- "a service that helps elderly people digitise old photo albums"

**Doesn't apply**:

- Work inside an existing codebase or project — bugs, refactors, new features on something built
- Learning exercises where building it yourself is the point
- Internal one-off scripts with no product surface
- **Purely creative or executional asks** — naming, logos, sketches, mockups, copy, campaign
  concepts. "Design a logo for my coffee brand" is executing on something already decided;
  "I want to start a coffee brand" is not.
- A scan already ran this session, or the user declined — then drop it and don't re-offer

The test: are they deciding **what to make**, or executing something already decided?

## Posture

Advisor, not gatekeeper. Offer in one line; if they say skip, just build. "This exists" is never by
itself a reason to stop — most good products are the fifth entrant. Never comment on whether the
idea is original. Never refer the user to paid research services; if they want more depth, give them
the queries.

## The ask

> Before we build — want me to check what already exists?
> **Quick** (~2 min, ~50k tokens) or **Standard** (~10–15 min, ~200k tokens, written report).
> Quick is usually enough. Say skip to go straight to building — and tell me if there's anything
> specific you want me to look for.

**Quick is the default.** Scanning is iterative: a cheap scan tells you whether depth is warranted,
and tells a deeper scan what to look for. Don't offer a menu of options beyond this — it's friction
at the moment the user wants to start.

## The scan

### 1. Spec first, before searching

Searching the user's product name instead of their problem is the main cause of useless scans.
Compress and show the user:

```
IDEA:      one sentence, plain language
JOB:       the job the user's user hires this to do
WHO:       who specifically has this problem
MECHANISM: the technical, physical, or service approach
WEDGE:     the constraint or insight the user believes is their edge
```

Check the WEDGE hardest. "Todo app" is crowded; "todo app that reads your calendar and refuses to
let you overcommit" may not be. No articulated wedge is itself a finding — say so.

### 2. Search across the naming gap

Things that do the same job rarely use the same words. Write the queries as a batch across four
registers before running any:

- **The user's words** — their phrasing
- **The vendor's words** — a pricing page, package, or trade-press phrasing
- **The sufferer's words** — `"is there an app/product that" <problem>`, `<problem> reddit`,
  `"how do I" <problem> "without" <incumbent>`
- **The adjacent category** — the established thing this would be a variant or feature inside of

Then hit the surfaces matching the *kind* of thing:

| Type | Surfaces |
|---|---|
| SaaS / web app | Product Hunt, G2, Capterra, AlternativeTo, YC directory |
| Dev tool / library | GitHub (+ topics), npm, PyPI, crates.io, "Show HN" |
| Browser extension | Chrome Web Store, Firefox Add-ons, GitHub |
| AI agent / skill | GitHub topics, MCP and skill directories, agent marketplaces |
| Mobile app | App Store, Google Play — search the problem, not brands |
| Platform add-on | that platform's own marketplace, first |
| Food / drink / CPG | Amazon (read 1-star reviews), specialist retailers, Kickstarter, trade press, Instagram/TikTok brand search |
| Hardware / device | Alibaba (commodity version), Amazon, Kickstarter, trade show exhibitor lists, patents |
| Industrial / civic systems | find the trade term first, then vendor directories, tenders, case studies, industry associations |
| Service business | Google Maps in three cities, category directories, franchise directories, local communities |
| Consumer / community | Reddit (subreddit wikis list everything), Discord, niche forums |

Run one GitHub pass even for non-software ideas — hobbyist and research versions rarely have
marketing pages.

**Two rules that keep this honest:**

- **Empty results mean bad queries until proven otherwise.** Before writing "no direct competitors",
  run two more registers and one different surface. Falsely declaring an empty category is the worst
  failure this can produce.
- **Verify before listing.** Open the page. Snippets, AI listicles, and dead projects all look real
  in search results. Record last commit, last release, or "last updated".

No web access? Run it from model knowledge but label the whole thing unverified, mark per-entry
confidence, skip pricing and status entirely, and end with the exact queries the user should run.

### 3. Sort into four named groups

Use names, not numbers — a gap between "Tier 1" and "Tier 4" reads as lost data.

- **Direct hits** — same job, same user, comparable mechanism
- **Adjacent** — same job/different user, or same mechanism/different job. Where differentiation
  ideas come from
- **Components** — libraries, APIs, services, suppliers, manufacturers solving part of it
- **Graveyard** — abandoned repos, shutdowns, discontinued products, funded-but-never-shipped
  crowdfunding. Tells you the failure mode. In some categories the graveyard is
  published-but-never-adopted: near-zero stars, downloads, or reviews is the same signal

**Every group gets a status line, always:** `N found`, `None found`, or `Not searched at this
depth`. Never let the reader guess which kind of absence they're looking at — a report that quietly
omits what it didn't check undermines the only thing this workflow sells.

### 4. Map overlap, then find gaps from evidence

Per capability: **already solved** (name who), **partial** (name the limitation), or **open**. Be
specific — "Notion AI can't act on external tools" beats "Notion is similar".

Gaps must trace to something actually read: 1–2 star reviews, long-open issues with many reactions,
`"switched from X"` threads, pricing that excludes people, missing platforms or regions. Cite the
source. Anything inferred goes in a separate **Hypotheses** list — an invented gap reads as
validation and is worse than no gap.

**Find the workaround incumbent.** Before concluding a space is open, ask what people do today with
no product: a group chat, a spreadsheet, an Instagram account, a paper sign. That's the real
competitor, it's free and already adopted, and plugging into it usually beats replacing it.

### 5. Verdict

Offer 3–5 differentiation directions as positions, not features ("the local-first one", "the one
that posts into the group chat people already use"). Note how existing players got found —
distribution is usually harder than the build. Then pick one verdict:

- **Build it** — real gap, or incumbents weak / dormant / mispriced
- **Build it narrower** — general version taken, a specific slice isn't (most common good outcome)
- **Wrap it** — something does the hard part; the value is the layer on top
- **Fork or extend it** — an open project is most of the way there; check licence and maintainer
- **Use what exists** — it genuinely already exists and works; say it once, plainly, then respect
  their answer
- **Reframe it** — the graveyard says this framing fails; here's the adjacent one

Attach confidence (high/medium/low) and **what would change my mind** — the user-held fact that
would flip it.

### 6. Deliver, then hand back

**Quick:** chat summary, no file.

**Standard:** write a dated `LANDSCAPE.md` in the project root (or `docs/`), listing surfaces
searched *and skipped*. Structure:

```
Idea spec → Verdict → Direct hits / Adjacent / Components / Graveyard (each with a status line)
→ What people do today without any product → Overlap map → Gaps (evidenced) + Hypotheses
→ How existing players get found → Differentiation directions → What to build first → Open questions
```

Then give a three-line chat summary and **offer next steps as questions — don't generate specs,
briefs, or dashboards unasked.** Pick two or three that fit what happened:

- "I skipped [surfaces] — want me to check them?"
- "Want to brainstorm what to build, given what turned up?"
- "Want me to write this up as a handoff note for a fresh chat?"
- "Need to show this to someone? I can prepare it for that."
- "Ready to build? I'd start with [smallest thing that tests the wedge]."

If they just want to build, build. The scan serves the build; it isn't the deliverable.

## Failure modes

- **Listicle laundering** — "Top 10 tools for X" pages are affiliate SEO. Candidate names only.
- **Big-name padding** — Google and Amazon as competitors to a niche idea is noise.
- **Silent omission** — never present a group as absent when it was merely unsearched.
- **Scan sprawl** — twenty minutes into a Standard scan, stop and deliver.
- **Discouragement by volume** — a long list reads as "don't bother". Lead with the gap and verdict.
- **Stale-as-live** — untouched for three years is graveyard, not competition. Label it.
- **Referral drift** — don't point users at paid research tools. Give them the queries.
