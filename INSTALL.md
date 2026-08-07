# Install

Pick the row that matches your tool. All four take under two minutes.

| Your tool | Use this file | Method |
|---|---|---|
| Claude Code | the plugin | `/plugin marketplace add` — one line |
| Claude Cowork / claude.ai | `SKILL-standalone.md` | Save as a skill |
| Codex, Cursor, Aider, Windsurf, Gemini CLI, Copilot | `AGENTS.md` | Copy into your project |
| ChatGPT, Gemini, anything else | `prompt.md` | Paste into custom instructions |

---

## Claude Code (recommended)

```
/plugin marketplace add n-any-i/is-there-a
/plugin install is-there-a@is-there-a
```

That's it. The skill triggers on its own the next time you describe something you want to build.

**To install manually instead** (no marketplace):

```bash
git clone https://github.com/n-any-i/is-there-a.git
cp -r is-there-a/skills/is-there-a ~/.claude/skills/
```

For a single project rather than everywhere, copy it to `.claude/skills/is-there-a/` inside that
project instead.

Verify with `/plugin` (it should be listed) or by typing `/is-there-a`.

---

## Claude Cowork / claude.ai

Saving a skill to your account stores **one file**, so use the single-file edition — it has the
reference material inlined and doesn't depend on the rest of the repo.

1. Open `SKILL-standalone.md`
2. Save it as a skill in your account
3. Start a new chat and describe something you want to build

If you want the full multi-file version instead, use Claude Code above.

---

## Codex, Cursor, Aider, Windsurf, Gemini CLI, GitHub Copilot

Copy `AGENTS.md` into the project you're working in:

```bash
curl -O https://raw.githubusercontent.com/n-any-i/is-there-a/main/AGENTS.md
```

Or append it to an `AGENTS.md` you already have:

```bash
cat AGENTS.md >> /path/to/your/project/AGENTS.md
```

Tool-specific locations, if you prefer them:

- **Cursor** — `.cursor/rules/is-there-a.mdc`
- **GitHub Copilot** — `.github/copilot-instructions.md`
- **Gemini CLI** — `GEMINI.md`, or import from `AGENTS.md`

Note that Claude Code reads `CLAUDE.md`, not `AGENTS.md`. If you're on Claude Code, use the plugin.

---

## ChatGPT, Gemini, or anything with an instructions box

Open `prompt.md` and copy one of the two blocks:

- **Full version** (~550 words) — for ChatGPT custom instructions, a Project, or a Gem
- **Compact version** (~130 words) — for tighter boxes, or the top of a long chat

Paste, save, and describe something you want to build.

---

## Checking it works

Three quick tests. Start a **new** conversation for each — a scan already run in a session won't
re-trigger.

1. **Should fire.** "I want to build a tool that turns my meeting notes into follow-up emails."
   → Expect an offer to scan, with time and token estimates.
2. **Should also fire (non-software).** "I want to start a brand of chewable coffee."
   → Same offer. If it doesn't fire, the description needs widening.
3. **Should NOT fire.** "Design a logo for my coffee brand" or "fix the bug in my checkout page."
   → Expect no scan offer. If it fires, the triggers are too greedy.

If any test misbehaves, edit the `description:` line at the top of `SKILL.md` — that line is what
decides when the skill loads, not the instructions below it.

---

## What it costs to have installed

Only the name and description stay loaded in every conversation — about 200 tokens, roughly a
paragraph. The instructions (~2,500 tokens) load only when the skill triggers, and the reference
files only when a scan actually needs them.

The scan itself is the real cost, and you're asked which size you want before it runs:

| Mode | Time | Tokens |
|---|---|---|
| Quick (default) | ~2 min | ~50k |
| Standard | ~10–15 min | ~150–300k |

---

## Uninstalling

- **Claude Code plugin:** `/plugin uninstall is-there-a@is-there-a`
- **Manual skill:** delete `~/.claude/skills/is-there-a/`
- **AGENTS.md / prompt:** delete the section you pasted
