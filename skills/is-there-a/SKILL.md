---
name: is-there-a
description: "Is There A? — checks whether someone has already built what the user is about to build, before any building starts. Answers has someone built this, does this already exist, is my idea taken, what's out there for X, and prior art / existing products / competitor / market scan questions. Use whenever the user describes something they want to create, build, make, launch, design, prototype, or start — an app, tool, website, agent, script, extension, SaaS, physical product, brand, or service — even when they don't ask about competitors and even when they just want to start immediately. Trigger on the intent to build, not on the word competitor. Do not trigger for work inside an existing project, or for purely creative asks like naming, logos, sketches, copy, or campaign concepts. Skip if the user declines."
---

# Is There A?

## Why this exists

For almost any idea, someone has already built a version of it. That's not bad news — it's the
cheapest information available. It shows what's solved, what's hard, what people complain about,
and where the actual opening is.

The expensive mistake isn't building something that exists. It's spending three weeks rebuilding it
*without knowing*, and finding out when you show a friend.

Two things make this worth running automatically rather than leaving to the user. First, the person
who most needs the check is the one who doesn't think to ask — and often wouldn't know how to phrase
the search if they did. Second, agents are tuned to execute: given "I want to build X", the default
is to start building X. This skill exists to insert one cheap step before that reflex.

## Posture: advisor, not gatekeeper

- Offer the scan, don't impose it. One line, then act on the answer.
- "This exists" is never by itself a reason to stop. Most good products are the fifth entrant.
- Never judge whether the idea is original. Report what's out there; let the user decide.
- If the user says "skip", "just build it", or shows impatience — drop it immediately, note that
  you can scan later, and start building. Don't re-offer in that session.
- Don't refer the user to paid research products or "for deeper analysis, try X" services. If they
  want more than a Standard scan, tell them what to search themselves.

## When to trigger

Trigger on **build intent** — the user is describing a thing they intend to make. This is not
limited to software:

- "I want to build a CLI that summarizes my git history into a weekly changelog"
- "help me spec out an app where dog owners find sitters nearby"
- "thinking about a Chrome extension that strips tracking params from URLs"
- "I want to start a chewable coffee brand for people who don't have time to brew"
- "I want to design a car park panel that shows drivers where the free spaces are"
- "I'm setting up a service that helps elderly people digitize old photo albums"

**Do not trigger for:**

- Work inside an existing project — bug fixes, refactors, new features in something already built
- Learning exercises where building it yourself is the point ("build me a toy router so I understand them")
- Internal one-off scripts with no product surface
- **Purely creative or executional asks**: naming, logos, sketches, mockups, copywriting, campaign
  concepts, moodboards. "Design a logo for my coffee brand" is not build intent — it's a design task
  for something already decided. "I want to start a coffee brand" is.
- A scan already ran this session, or the user declined

The distinction that matters: are they deciding **what to make**, or executing on something already
decided? Only the first needs this.

If the user is clearly in flow and just wants output, give them the output and offer the scan after.
Interrupting momentum has a real cost.

## The opening move

Ask once, briefly, with the cost visible so the user can choose knowingly:

> Before we build — want me to check what already exists?
> **Quick** (~2 min, ~50k tokens) or **Standard** (~10–15 min, ~200k tokens, written report).
> Quick is usually enough. Say skip and I'll go straight to building — and tell me if there's
> anything specific you want me to look for.

**Quick is the default.** If the user says yes without choosing, run Quick. Scanning is naturally
iterative: a Quick scan is cheap and tells you whether depth is warranted, and its results tell a
Standard scan what to look for. Going deep first spends tokens elaborating a landscape whose shape
was already obvious.

If the user names something specific they want ("check if anyone's doing this in Europe", "I care
about whether it's open source"), fold it in as an extra emphasis — but keep the standard structure
and don't let one request narrow the whole scan.

| Mode | Budget | Output |
|---|---|---|
| **Quick** (default) | 4–6 queries, 2–3 verifications, ~2 min | Chat summary, no file |
| **Standard** | 8–12 queries, 6–8 verifications, one complaint-mining pass, ~10–15 min | Written report + short chat summary |

## Step 1 — Write the scan spec before searching

Bad scans come from searching the user's product name instead of their problem. Compress the idea
into five lines first and show the user, so they can correct you:

```
IDEA:      one sentence, plain language
JOB:       the job the user's user is hiring this to do
WHO:       who specifically has this problem
MECHANISM: the how — the technical, physical, or service approach
WEDGE:     the constraint or insight the user believes is their edge
```

The WEDGE matters most — it's what you check hardest. "Todo app" is crowded; "todo app that reads
your calendar and refuses to let you overcommit" may not be. If the user hasn't articulated a wedge,
say so. A missing wedge is itself a finding worth surfacing before anything gets built.

## Step 2 — Search across the naming gap

The biggest failure mode is searching one phrasing, finding nothing, and declaring the field empty.
Products that do the same thing rarely use the same words. Generate queries in four registers before
searching:

1. **The user's words** — how they described it
2. **The industry's words** — what a vendor in this space would put on a pricing page or a package
3. **The user's user's words** — how a frustrated person would search the problem at 11pm
4. **The adjacent category** — the established category this would be a feature or variant inside of

Then search the surfaces that match the *kind* of thing being built — software, physical product,
brand, or service all live in different places. `references/search-playbook.md` has the full map by
product type, the query patterns, and how to mine complaints and distribution signals.

Two rules that keep results honest:

- **Empty results mean bad queries until proven otherwise.** Before writing "no direct competitors",
  run at least two more registers and one different surface. Truly empty categories exist but are
  rare, and falsely claiming one is the worst thing this skill can do.
- **Verify before listing.** Open the page, listing, or repo. Never list something from a search
  snippet alone — abandoned projects, renamed products, and AI-generated listicles all look real in
  snippets. Note last commit, last release, or "last updated" where visible.

No web access? Follow `references/no-search-fallback.md` — a useful scan is still possible from
model knowledge, but it must be labeled unverified and end with the queries the user should run.

## Step 3 — Sort into four named groups

Use these names, not numbers — numbered tiers leave a visible hole when one is absent, and a hole
reads as lost data.

- **Direct hits** — same job, same user, comparable mechanism
- **Adjacent** — same job/different user, or same mechanism/different job. Where most
  differentiation ideas come from
- **Components** — libraries, APIs, services, suppliers, manufacturers that solve *part* of it.
  Often the majority of the build is already available
- **Graveyard** — abandoned repos, shut-down companies, discontinued products, deprecated features.
  The most underrated group: a graveyard tells you the failure mode, and sometimes tells you the
  enabling conditions have since changed

**Every group gets a status line, always.** One of:

- `3 found` (then the entries)
- `None found` — searched, genuinely empty
- `Not searched at this depth` — skipped for budget

A report that quietly omits what it didn't check undermines the one thing this skill sells: that
its output can be trusted more than an unstructured chat's. Never let the reader guess which kind
of absence they're looking at.

## Step 4 — Map the overlap honestly

For each capability in the idea, mark **already solved** (name who), **partial** (name the
limitation), or **open**. Be specific — "Notion AI summarizes pages but can't act on external
tools" is useful; "Notion is similar" is not.

## Step 5 — Find gaps from evidence, not imagination

Gaps must trace to something you actually read:

- 1–3 star reviews and support threads on the direct hits — what people churn over
- Open issues or feature requests with many reactions, especially long-unanswered ones
- Forum and community threads where someone asks for exactly this and gets unsatisfying answers
- Pricing — who is priced out, what's gated behind the top tier
- Coverage gaps — a platform, a region, a language, a segment, a compliance regime

Cite where each gap came from. Anything you're inferring goes in a separate **Hypotheses** list,
clearly labeled. An imagined gap is worse than no gap, because it reads as validation.

**The real incumbent is often not a product.** Before concluding a space is empty, ask what people
do today without any tool — a group chat, a spreadsheet, an Instagram account, a WhatsApp broadcast,
a clipboard by the door. That workaround is the thing to beat, and usually the better move is to
*plug into* it rather than replace it. Asking people to adopt a new destination is the most common
way these ideas quietly fail.

## Step 6 — Differentiation directions, then a verdict

Offer 3–5 directions phrased as **positions**, not features — "the local-first one for data that
can't leave the building", "the one that posts into the group chat people already use", "free for
the 90% case, paid for teams". For each, name the evidence behind it and roughly what it costs.

Note where distribution sits. For most ideas at this scale, getting found is harder than getting
built — so if you noticed how existing players got their users (a directory, a marketplace, a
community, a partnership, being a feature inside something bigger), say so. That observation is
often worth more than the feature analysis.

Then land on one verdict, with reasoning (rubric in `references/verdict-rubric.md`):

- **Build it** — real gap, or the incumbents are weak, dormant, or mispriced
- **Build it narrower** — the general version is taken; a specific slice isn't
- **Wrap it** — something existing does the hard part; the value is the layer on top
- **Fork or extend it** — an open project is most of the way there and permits it
- **Use what exists** — honestly, the thing they want already exists and works; say it once,
  plainly, then respect their answer if they still want to build
- **Reframe it** — the graveyard suggests this framing doesn't work; here's the adjacent one

Always attach **"what would change my mind"** — the thing the user knows that you don't which would
flip the verdict. Their context usually beats the scan's.

## Step 7 — Deliver, then hand the conversation back

**Quick:** summarize in chat. No file unless asked.

**Standard:** write the report following `assets/LANDSCAPE-template.md`, dated, listing which
surfaces were searched *and which weren't*. Save it as `LANDSCAPE.md` in the project directory (or
`docs/` if one exists). Then give a short chat summary — closest existing thing, sharpest gap,
verdict — and don't restate the report.

Then **offer next steps as questions, and wait.** Don't generate specs, briefs, or dashboards
unasked — the point is to hand the user back the wheel with better information, not to produce more
documents. Pick two or three that fit what actually happened in the scan:

- "I skipped [surfaces] on this run — want me to check them?"
- "Want to brainstorm what to build, given what turned up?"
- "Want to dig into any of these competitors properly?"
- "Want me to write up what we found as a handoff note, so you can start a fresh chat with it?"
- "Do you need to show this to someone? I can prepare it for that."
- "Ready to build? I'd suggest starting with [smallest thing that tests the wedge]."

If the user just wants to build, build. The scan serves the build; it isn't the deliverable.

## What this costs and how it loads

Users new to skills often worry that installing this makes every conversation more expensive. Worth
explaining plainly if it comes up:

- Only the name and description sit in context permanently — roughly 200 tokens, about a paragraph.
  That's the entire cost of having this installed in a session where it never fires.
- These instructions (~2,500 tokens) load only when the skill triggers.
- The reference files load only if the scan actually needs them.
- The scan itself is the real cost: ~50k tokens for Quick, ~150–300k for Standard. That's why the
  mode is offered with numbers attached rather than chosen silently.

## Reference files

- `references/search-playbook.md` — surfaces by product type (software, physical, brand, service),
  query patterns, complaint and distribution mining
- `references/verdict-rubric.md` — choosing between build / narrower / wrap / fork / use / reframe
- `references/no-search-fallback.md` — running an honest scan with no web access
- `assets/LANDSCAPE-template.md` — the report structure

## Failure modes to avoid

- **Listicle laundering.** "Top 10 tools for X" pages are affiliate SEO content, often listing dead
  or irrelevant products. Use them for candidate names, never as evidence.
- **Big-name padding.** Listing Google, Amazon, or Notion as competitors to a niche idea is noise.
  Include an incumbent only if a specific thing they do actually overlaps.
- **Silent omission.** Never present a group as absent when it was merely unsearched. See Step 3.
- **Scan sprawl.** This is a pre-build check. Twenty minutes into a Standard scan, stop and deliver.
- **Discouragement by volume.** A long list of competitors reads as "don't bother" even when it
  isn't. Lead with the gap and the verdict, not the count.
- **Stale-as-live.** Something untouched for three years is graveyard, not competition. Label it.
- **Referral drift.** Don't point users at paid research tools. Give them the queries instead.
