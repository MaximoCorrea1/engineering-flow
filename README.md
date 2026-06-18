# Engineering Flow

A curated **Flowy** Flow: hand-picked best-of-breed engineering skills + a `FLOW.md` router. Install it and FLOW.md routing makes the right skill fire at each phase of building a feature — brainstorm the spec, write the plan, drive it with tests, debug at the root, review the diff, verify, and ship safely.

This is the recommended **cross-source successor to `superpowers-flow`**. Where `superpowers-flow` wraps only obra/superpowers, Engineering Flow keeps the proven superpowers spine (brainstorm → plan → TDD → debug → verify) and adds a best-of-breed review skill from compound-engineering and a launch skill from agent-skills, so the full arc through code review and shipping is covered from one Flow. `superpowers-flow` remains available and supported — install it if you want the single-source superpowers bundle.

## Install

```
/flowy:engineering-flow
```

## What it routes

The arc: **brainstorm → plan → TDD → debug → review → verify → ship.**

| Phase | Skill | Source |
|---|---|---|
| Brainstorm the spec | `brainstorming` | obra/superpowers |
| Write the plan | `writing-plans` | obra/superpowers |
| Drive with tests (RED→GREEN) | `test-driven-development` | obra/superpowers |
| Debug at the root | `systematic-debugging` | obra/superpowers |
| Review the diff | `ce-code-review` | EveryInc/compound-engineering |
| Verify before "done" | `verification-before-completion` | obra/superpowers |
| Ship to production | `shipping-and-launch` | addyosmani/agent-skills |

## Credits & license

Skills are vendored verbatim from their upstream authors — see [ATTRIBUTION.md](./ATTRIBUTION.md) for per-skill author + license + source + SHA. The five spine skills are by Jesse Vincent (obra/superpowers, MIT); `ce-code-review` is by Every (EveryInc/compound-engineering-plugin, MIT); `shipping-and-launch` is by Addy Osmani (addyosmani/agent-skills, MIT). FLOW.md routing by Flowy. Because every vendored skill is MIT, **this Flow is licensed MIT as a whole** (see [LICENSE](./LICENSE)).
