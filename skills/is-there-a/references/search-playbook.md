# Search Playbook

Where to look, what to type, and how to turn results into evidence.

## Contents

1. [Query construction](#1-query-construction)
2. [Surfaces by product type](#2-surfaces-by-product-type)
3. [Mining complaints and gaps](#3-mining-complaints-and-gaps)
4. [Mining distribution](#4-mining-distribution)
5. [Finding the graveyard](#5-finding-the-graveyard)
6. [Judging whether something is alive](#6-judging-whether-something-is-alive)
7. [Budget by mode](#7-budget-by-mode)

---

## 1. Query construction

Write the queries as a batch before running any of them — it prevents the tunnel vision of chasing
the first result. Four registers:

**Register A — the user's words.** Their exact phrasing, in case the category already has that name.

**Register B — the vendor's words.** How this would appear on a pricing page, a package, a catalogue
listing, or a trade publication. Translate casual phrasing into industry phrasing: "app that nags me
about spending" → "budget alerts", "personal finance notifications"; "chewy coffee thing" →
"caffeinated chew", "energy chew", "functional confectionery".

**Register C — the sufferer's words.** How someone with the problem would search at 11pm, including
the frustration framing:

- `"is there an app that" <problem>` / `"is there a product that" <problem>`
- `"how do I" <problem> "without" <annoying incumbent>`
- `<problem> reddit`
- `"anyone know a" <thing> <problem>`

This register finds threads where people ask for exactly this — which surfaces both existing answers
and evidence that the demand is real.

**Register D — the adjacent category.** The established category this would be a variant or feature
inside of: `<incumbent> <feature>`, `<incumbent> alternative`, `<category> for <specific user>`.
Often the answer is "this exists as a checkbox inside something bigger", which is a very different
competitive situation from a standalone rival.

**Useful modifiers**

- `site:github.com`, `site:reddit.com`, `site:news.ycombinator.com`, `site:producthunt.com`
- `"Show HN"` + concept — high signal for indie software
- `"open source" <concept>`, `<concept> alternative`, `<concept> "vs"` (comparison pages reveal a
  whole competitive set at once)
- For physical goods: `<concept> "buy"`, `<concept> amazon`, `<concept> kickstarter`, `<concept> patent`
- Year-bounded (`2026`) for freshness; omit the year deliberately when hunting the graveyard

---

## 2. Surfaces by product type

Search general web plus the surfaces matching the idea's shape. Two to four beyond general web is
usually enough.

### Software and digital

**Web app / SaaS** — Product Hunt · G2 · Capterra · AlternativeTo · Y Combinator directory ·
Crunchbase · IndieHackers

**Developer tool / library / CLI** — GitHub (search + topics) · npm · PyPI · crates.io ·
pkg.go.dev · Homebrew · awesome-* lists in the domain · "Show HN"

**Browser extension** — Chrome Web Store · Firefox Add-ons · Edge Add-ons · GitHub

**AI agent / skill / prompt tool** — GitHub topics · MCP and skill directories · agent marketplaces ·
Hugging Face Spaces · Product Hunt AI category

**Mobile app** — App Store and Google Play, searching the *problem phrase* rather than brand names ·
app-review threads in relevant communities

**Platform add-on** (Slack, Notion, Shopify, Salesforce, VS Code, Obsidian, Figma…) — that
platform's own marketplace, first. A native add-on that already ships is a harder competitor than
any standalone product.

### Physical products, brands, and services

These are easy to under-search because they're less indexed than software. Give them a surface or
two more than feels necessary.

**Consumer packaged goods / food / beverage / supplements** — Amazon (and read the 1-star reviews) ·
Thrive/iHerb/Holland & Barrett-style specialist retailers · Kickstarter and Indiegogo (where most
CPG launches start) · trade press for the category (e.g. food & beverage industry news) ·
Instagram and TikTok brand search — many small brands exist only there · retail category pages at
the chains that would stock it

**Hardware / device / equipment** — Alibaba and Made-in-China for the commodity version (if it's a
$40 white-label item, that's decisive) · Amazon · Kickstarter · trade show exhibitor lists for the
industry · patent search if the mechanism is novel · vendor directories and industry buyer's guides

**Industrial, civic, or B2B installed systems** (signage, sensors, kiosks, fleet, facilities) — the
industry's own vocabulary is essential here and rarely matches consumer phrasing; find the trade
term first, then search vendor directories, procurement/tender records, case studies, and industry
association member lists. Municipal and campus systems are often documented in public tender
documents and press releases.

**Service business** — Google Maps / local listings in three different cities · Yelp and category
directories · franchise directories (a franchise system means the model is proven and taken) ·
Thumbtack/TaskRabbit-style marketplaces · relevant subreddits and local community groups

**Marketplace / two-sided** — search each side separately; supply and demand often have different
existing solutions, and the real incumbent is frequently a Facebook group or a spreadsheet

**Community / consumer** — Reddit (the subreddit wiki and sidebar often lists every tool or product
in the space) · Discord servers · niche forums

### One code-surface pass, always

Even for non-software ideas, one GitHub pass is cheap and sometimes reveals a hobbyist version, an
internal tool, or a research prototype that never got a marketing page. For software ideas it's
mandatory.

---

## 3. Mining complaints and gaps

Gaps must trace to something read, not imagined. Highest-yield sources, roughly in order:

1. **Low-star reviews of the direct hits.** 1–2 stars on Amazon, app stores, G2, Capterra, Trustpilot.
   Repeated words matter — the same complaint three times is a wedge.
2. **Open issues and feature requests** with many reactions, especially long-unanswered ones.
3. **Churn threads** — `"<product> alternative"`, `"switched from <product>"`, `"why I stopped using
   <product>"`, `"<product> too expensive"`.
4. **Pricing.** Note the cheapest paid tier and what's locked behind the top one. Price exclusion is
   one of the most reliable openings for a new entrant.
5. **Coverage lists** — supported platforms, regions, languages, integrations. Who's excluded.
6. **"Known limitations" pages and changelogs** — gaps written by the incumbent itself. Changelog
   cadence also tells you whether anyone is still investing.

Record the source for every gap. In the report, a gap with a link is a finding; a gap without one is
a guess, and goes in the Hypotheses list.

### Ask what people do with no product at all

Before concluding a space is open, find the workaround. A group chat, a spreadsheet, an Instagram
account, a paper sign, a WhatsApp broadcast, an intern. Search for it directly: `<problem>
spreadsheet template`, `<problem> whatsapp group`, `how people currently <problem>`. The workaround
is the true incumbent and it is usually free, already adopted, and where the users already are —
which often makes integrating with it a better move than replacing it.

---

## 4. Mining distribution

For ideas at this scale, getting found is usually harder than getting built. While you're on the
competitors' pages anyway, note how they got their users — it costs almost nothing and is often the
most actionable thing in the report:

- Where are they listed? (directories, marketplaces, awesome-lists, app stores, retailers)
- Did they launch somewhere specific? (Product Hunt, Kickstarter, a subreddit, a trade show)
- Are they a feature inside a bigger platform, or standalone?
- Do they sell to the end user or to an institution that buys on their behalf?
- Is there an obvious community where this category's users congregate?

One or two sentences in the report is enough. The point is to tell the user where their users
actually are.

---

## 5. Finding the graveyard

The most instructive group and the easiest to skip:

- Repos with the concept in the name and no commits for 2+ years — read the README's ambition and
  the last issues for why it stalled
- `"shutting down" <concept>`, `"sunsetting" <concept>`, `"<product> post-mortem"`,
  `"discontinued" <product>`
- Community threads about a product that no longer exists
- Crowdfunding campaigns that funded and never shipped — extremely common for physical products
- Companies that pivoted away from the concept

Two failed attempts at the same thing means asking *why* before starting the third. Sometimes the
answer is "they were early and the enabling conditions now exist", which is the best finding
available.

Note: in some categories — published agent skills, app-store apps, small brands — the graveyard
isn't dead products but **published-and-never-adopted** ones. Near-zero stars, downloads, reviews,
or followers is the same signal in a different form, and worth reporting as such.

---

## 6. Judging whether something is alive

Before listing anything as a direct hit, check for a pulse:

| Signal | Alive | Dead / stale |
|---|---|---|
| Last commit or release | < 6 months | > 18 months |
| Changelog, blog, or social | posts this year | last post 2+ years ago |
| Pricing or product page | loads, current | 404, or "contact us" only |
| Store listing | updated this year | "last updated" 3 years ago |
| Stock / availability (physical) | in stock, ships | permanently out of stock |
| Support responses | within weeks | unanswered for months |

Label each entry **active**, **maintenance**, or **dormant**. A dormant product with users is an
opportunity — their users are looking for a replacement — not a competitor.

---

## 7. Budget by mode

**Quick (~2 min, ~50k tokens)** — 4–6 queries across registers A, C and one of B/D. General web plus
one matching surface. 5–8 candidates, verify the top 2–3. Chat summary, no file. Say explicitly
which surfaces went unsearched.

**Standard (~10–15 min, ~150–300k tokens)** — 8–12 queries across all four registers. General web
plus 2–4 matching surfaces, plus one code-surface pass. 12–20 candidates, verify 6–8, one
complaint-mining pass on the two closest hits, one graveyard pass, light distribution notes.
Written report.

Stop when new queries stop producing new names. That saturation point — not the clock — is the real
signal that the scan is done.
