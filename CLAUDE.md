# Skills Repository Guide

Skills are organized into bucket folders under `skills/`:

- `engineering/`: daily code, architecture, and shipping checks
- `productivity/`: daily non-code workflow tools
- `misc/`: kept around but rarely used, not promoted
- `in-progress/`: experimental skills meant for local iteration, not shipped in the plugin
- `deprecated/`: retired skills

## Promoted buckets and manifests

Every skill in `engineering/` or `productivity/` (the **promoted** buckets) must have:

1. An entry in the top-level `README.md` (linking the skill name to its `SKILL.md`).
2. An entry in its bucket `README.md` (grouped under **Model-invoked** or **User-invoked**).
3. An entry in `.claude-plugin/plugin.json`'s `skills` array.
4. A human-facing doc page at `docs/<bucket>/<skill-name>.md` with four sections: **What it does**, **When to reach for it**, **Common questions**, and **It's working if**.

Skills in `misc/`, `in-progress/`, and `deprecated/` stay out of the top-level `README.md`, `.claude-plugin/plugin.json`, and `docs/`. Non-promoted bucket `README.md`s use a flat list.

## Invocation metadata

Every `SKILL.md` is either:

- **User-invoked**: set `disable-model-invocation: true` in `SKILL.md` frontmatter and `policy.allow_implicit_invocation: false` in `agents/openai.yaml`. Write a one-line human-facing `description`.
- **Model-invoked**: omit both flags and write a model-facing `description` with trigger branches.

Keep `agents/openai.yaml` beside every `SKILL.md` with `interface.display_name` and `interface.short_description`.

## Local linking

Run `./scripts/link-skills.sh` after adding, renaming, or removing any skill. It links every skill outside `deprecated/` and `misc/` into `~/.claude/skills`, `~/.agents/skills`, and `~/.gemini/config/skills`.

## Writing style

- Follow the `writing-for-agents` discipline when editing any `SKILL.md`.
- Avoid em-dashes across prose (`SKILL.md`, `docs/`, `README.md`); rewrite with commas, colons, periods, or parentheses instead.
- Subagent steps should specify a fresh context window so the harness does not inherit noisy parent context.
