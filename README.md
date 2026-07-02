# Yinc Skills

Shared [Claude Code](https://claude.com/claude-code) skills for Yinc, packaged as a plugin marketplace.

A *skill* is a self-contained instruction set (a `SKILL.md` file, plus any supporting files) that Claude loads on demand. This repo is both a **marketplace** (`yinc`) and the **plugin** it hosts (`yinc-skills`), which bundles every skill below.

## Install

From a terminal:

```sh
claude plugin marketplace add yinc-studio/skills
claude plugin install yinc-skills@yinc
```

Or, inside Claude Code, run the equivalent slash commands:

```
/plugin marketplace add yinc-studio/skills
/plugin install yinc-skills@yinc
```

Once installed, skills are namespaced under the plugin and invoked as `/yinc-skills:<skill-name>` (e.g. `/yinc-skills:yinc-orchestrate`).

## Skills

| Skill | Invoke | Description |
|-------|--------|-------------|
| [`yinc-orchestrate`](skills/yinc-orchestrate/) | `/yinc-skills:yinc-orchestrate` | Act as orchestrator for the session: route each unit of work to a subagent on the best-fit model, then integrate the results. |

## Updating

Bump the `version` in [`.claude-plugin/plugin.json`](.claude-plugin/plugin.json) and the matching entry in [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json) when you change a skill, so installed users receive the update. Users refresh with:

```sh
claude plugin marketplace update yinc
```

## Adding a skill

1. Create `skills/<skill-name>/SKILL.md` with YAML frontmatter (`name`, `description`) followed by the instructions.
2. Add a row to the table above.
3. Bump the plugin version (see [Updating](#updating)).

## Repo layout

```
.
├── .claude-plugin/
│   ├── marketplace.json   # marketplace manifest (name: yinc)
│   └── plugin.json        # plugin manifest (name: yinc-skills)
├── skills/
│   └── yinc-orchestrate/
│       └── SKILL.md
└── README.md
```

See Anthropic's [plugin marketplace docs](https://code.claude.com/docs/en/plugin-marketplaces) for the full schema.
