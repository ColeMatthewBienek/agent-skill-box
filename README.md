# agent-skill-box

Personal box for agent skills. Same delegation philosophy, packaged for two agents:

- **[`efficient-fable`](efficient-fable/)** — for **Claude Code** (Claude Fable as orchestrator)
- **[`efficient-sol`](efficient-sol/)** — for **Codex** (Sol, Extra High reasoning, as orchestrator)

Both teach the model to keep judgment, architecture, and final review for itself while
delegating token-heavy research, coding, and testing to cheaper subagents.

## For Claude Code users

Install `efficient-fable`:

```sh
npx skills add ColeMatthewBienek/agent-skill-box --skill efficient-fable -a claude-code
```

This symlinks/copies it into `.claude/skills/efficient-fable/` (add `-g` to install
globally to `~/.claude/skills/` instead). Once installed, invoke it with `/efficient-fable`.

`efficient-fable` is sourced from
[BuilderIO/skills](https://github.com/BuilderIO/skills/tree/main/skills/efficient-fable),
credit to Builder.io for the original. Since it's published there upstream, you can
alternatively use the BuilderIO installer, which can also wire up an `AGENTS.md` /
`CLAUDE.md` instruction block automatically:

```sh
npx @agent-native/skills@latest add --skill efficient-fable --update-instructions
```

See [`efficient-fable/README.md`](efficient-fable/README.md) for details on what the skill does.

## For Codex users

Install `efficient-sol`:

```sh
npx skills add ColeMatthewBienek/agent-skill-box --skill efficient-sol -a codex
```

This installs it into `.agents/skills/efficient-sol/` (project scope) or
`~/.codex/skills/` with `-g` (global scope).

`efficient-sol/agents/openai.yaml` additionally defines a Codex custom-agent entry point
(display name, description, and a default prompt referencing `$efficient-sol`) for
runtimes that support registering named agents from that file.

See [`efficient-sol/SKILL.md`](efficient-sol/SKILL.md) for the full delegation pattern.

## Notes

- Both skills follow the [Agent Skills spec](https://agentskills.io) (`SKILL.md` with
  `name` + `description` frontmatter), so the same `npx skills add ...` command works for
  either — just swap `--skill` and `-a`/`--agent`.
- `npx skills list --list` (or `add ... --list`) against this repo shows both skills without
  installing anything, if you just want to check what's here.
