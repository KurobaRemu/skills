# Personal Agent Skills

Personal collection of small, composable skills for real engineering, organized following the [`mattpocock/skills`](https://github.com/mattpocock/skills) layout.

## Installation

### Local development (symlink into local harnesses)

```bash
./scripts/link-skills.sh
```

Links active skills (`engineering/`, `productivity/`, `in-progress/`) into `~/.claude/skills`, `~/.agents/skills`, and `~/.gemini/config/skills`.

### Claude Code / Codex / npx skills

Once pushed to GitHub (`KurobaRemu/skills`):

```bash
# Claude Code marketplace install
/plugin install kurobaremu-skills --marketplace KurobaRemu/skills

# Or via skills.sh
npx skills add KurobaRemu/skills
```

Or via marketplace manifests in [`.claude-plugin/`](./.claude-plugin).

## Skills

### Engineering

#### Model-invoked

- [whiteboard-defense](./skills/engineering/whiteboard-defense/SKILL.md): Run a blind oral whiteboard defense to verify architectural understanding before shipping customer-facing work. ([docs](./docs/engineering/whiteboard-defense.md))

#### User-invoked

_None yet._

### Productivity

_None yet._
