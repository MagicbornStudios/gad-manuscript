# Agent guide — gad-manuscript

This project is managed under the **GAD framework**. Use `gad` CLI for all planning context.

## Context re-hydration

```sh
gad state --projectid gad-manuscript
gad tasks --projectid gad-manuscript
gad decisions --projectid gad-manuscript
```

Or full snapshot:
```sh
gad snapshot --projectid gad-manuscript
```

## Planning loop

1. `gad state --projectid gad-manuscript` — read current phase and next action
2. Pick one planned task from `gad tasks --projectid gad-manuscript`
3. Implement it
4. Update `.planning/TASK-REGISTRY.xml` — mark task done
5. Update `.planning/STATE.xml` — update next-action
6. `gad sink sync` — propagate to docs sink
7. Commit

## Planning files

| File | Purpose |
|------|---------|
| `.planning/STATE.xml` | Current phase, milestone, status, next-action |
| `.planning/ROADMAP.xml` | Phase breakdown |
| `.planning/TASK-REGISTRY.xml` | All tasks by phase with status |
| `.planning/DECISIONS.xml` | Architectural decisions |

## Docs sink

Planning docs compile to: `apps/portfolio/content/docs/gad-manuscript/planning/`

```sh
gad sink sync                                # compile all projects
gad sink status --projectid gad-manuscript   # check sync state
```

## Purpose

gad-manuscript generates in-world lore content for the Magicborn fiction project using the
`content-skill = "gad-manuscript"` pipeline defined in planning-config.toml.
