# Install

| Your tool | Method |
|---|---|
| [Claude Code](#claude-code) | One-line plugin install |
| [Claude apps — Cowork, chat, desktop](#claude-apps--cowork-chat-desktop) | Upload a zip in Settings |
| [Codex, Cursor, Aider, Windsurf, Gemini CLI, Copilot](#codex-cursor-and-other-agents) | Copy `AGENTS.md` into your project |
| [ChatGPT, Gemini, anything else](#chatgpt-gemini-and-anything-else) | Paste from `prompt.md` |

---

## Claude Code

```
/plugin marketplace add n-any-i/is-there-a
/plugin install is-there-a@is-there-a
```

Manual alternative:

```bash
git clone https://github.com/n-any-i/is-there-a.git
cp -r is-there-a/skills/is-there-a ~/.claude/skills/
```

Use `.claude/skills/` inside a project instead of `~/.claude/skills/` to scope it to that project.
Check it's there with `/plugin`, or type `/is-there-a`.

---

## Claude apps — Cowork, chat, desktop

1. Download **[`dist/is-there-a.zip`](dist/is-there-a.zip)**.
2. In Claude: **Settings → Capabilities** and turn on *Code execution and file creation* (skills
   need it).
3. **Settings → Customize → Skills → + → Create skill**, upload the zip, toggle it on.

The zip contains the full skill — `SKILL.md` plus its reference files. Don't rezip it from a
different folder level; the archive needs the `is-there-a/` folder at its root.

`SKILL-standalone.md` is the same method inlined into one file. Use it only if you're pasting the
skill somewhere that takes a single file.

---

## Codex, Cursor, and other agents

Copy `AGENTS.md` into the project you're working in:

```bash
curl -O https://raw.githubusercontent.com/n-any-i/is-there-a/main/AGENTS.md
```

Or append it to an `AGENTS.md` you already have:

```bash
cat AGENTS.md >> /path/to/your/project/AGENTS.md
```

Tool-specific alternatives: **Cursor** → `.cursor/rules/is-there-a.mdc` · **Copilot** →
`.github/copilot-instructions.md` · **Gemini CLI** → `GEMINI.md`. Claude Code reads `CLAUDE.md`, not
`AGENTS.md` — use the plugin above instead.

---

## ChatGPT, Gemini, and anything else

Copy a block from [`prompt.md`](prompt.md) into custom instructions, a Project, or a Gem — the full
version (~550 words) where you have room, the compact one (~130 words) where you don't.

---

## Check it works

Three prompts, each in a **new** conversation (a scan already run in a session won't re-trigger).

1. **Should fire** — "I want to build a tool that turns my meeting notes into follow-up emails."
2. **Should also fire** — "I want to start a brand of chewable coffee." *(If not, the description
   needs widening for non-software ideas.)*
3. **Should NOT fire** — "Design a logo for my coffee brand." *(If it fires, the triggers are too
   greedy.)*

Misbehaving? Edit the `description:` line at the top of `SKILL.md`. That line decides when the skill
loads — not the instructions below it.

---

## What it costs

Only the name and description stay loaded in every conversation — about 200 tokens. Instructions
(~2,500) load on trigger; reference files load only when a scan needs them. The scan itself is the
real cost, and you choose the size: **Quick** ~2 min / ~50k tokens, **Standard** ~10–15 min /
~150–300k.

---

## Uninstall

Claude Code plugin → `/plugin uninstall is-there-a@is-there-a` · Manual skill → delete the
`is-there-a` folder · Claude apps → toggle off or delete in Settings → Skills · AGENTS.md or prompt
→ delete the pasted section.
