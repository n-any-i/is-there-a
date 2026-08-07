# No-Search Fallback

Some agents and sessions have no web access. A scan is still worth running — a model has read a lot
of the internet and can usually name the incumbents in most categories — but the honesty
requirements go up sharply, because unverifiable recall is where invented competitors come from.

## What changes

**Label the whole report.** At the top, unmissable:

> ⚠️ Offline scan — no web access. Everything below is from model knowledge with a cutoff, not
> verified sources. Products may have shut down, launched, changed price, or been renamed. Treat
> every entry as a lead to verify, not a fact. Verification queries are at the end.

**Only name what you're confident about.** "I'm confident this category exists and includes products
like X and Y" — not an invented feature comparison for X. A fabricated competitor is worse than an
admitted blind spot, because the user may abandon a good idea over a product that doesn't exist.

**Mark confidence per entry.**

- **High** — well-known, stable for years, you'd bet on its existence
- **Medium** — you recall it but not its current state, price, or whether it still ships
- **Low** — a vague sense something like this exists; a search lead only

**Say nothing about pricing, funding, or current status.** These change fastest and are the most
likely to be wrong. Mark the field "verify" rather than guessing.

**State the time horizon.** Note the knowledge cutoff, and that fast-moving categories — anything
AI-adjacent, anything in consumer trends — turn over in months. There, an offline scan is close to
worthless for direct hits, though still useful for the structural work below.

## What still works well offline

Often the most valuable output, and none of it depends on fresh data:

- **The scan spec** — idea / job / who / mechanism / wedge
- **The naming gap** — generating the four vocabularies the user should search in. For someone who
  doesn't know how to phrase the search, this alone is worth the run
- **Category structure** — what kinds of solutions exist, how the space segments, which incumbents
  plausibly have this as a feature
- **The workaround incumbent** — what people do today with no product at all
- **Known failure modes** — why products in this category typically struggle
- **Differentiation directions** — positions that would be defensible regardless of who holds them

## Deliver a verification kit

The most useful thing an offline scan produces is a short list of exactly what to search:

```
## Verify this scan (10 minutes)

Queries:
1. <problem in the sufferer's words>
2. <industry term> 2026
3. site:github.com <concept>
4. "<closest named product>" alternative
5. site:reddit.com "is there a" <problem>

Surfaces: <2-4 named surfaces from the search playbook, matched to the product type>

Check specifically:
- Is <named product> still active, and what does it cost now?
- Does <incumbent platform> now ship this as a built-in feature?
- Anything in this category launched in the last 6 months?
```

Then offer: "Paste anything you find back here and I'll fold it into the analysis." That turns a
weak scan into a collaborative one.

## Hold the verdict loosely

Offline, prefer a conditional: "If the searches below turn up fewer than three active products,
build it narrower as described; if they turn up a well-maintained open project, extending it is
likely faster." Give the branch, not the ruling.
