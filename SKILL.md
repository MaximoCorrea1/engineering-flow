---
name: engineering-flow
description: Ship features the disciplined way: brainstorm, plan, build test-first, debug at the root, review, and ship with care.
version: 0.1.0
license: MIT
domain: software-engineering
---

# Engineering Flow

A curated **Flowy** Flow: best-of-breed engineering skills, drawn from more than one upstream source and wired into a `FLOW.md` router that fires the right one at each phase of building a feature. Brainstorm the spec, write the plan, drive it with tests, debug failures at the root, review the diff, verify against reality, then ship it safely.

This is the recommended cross-source **successor to `superpowers-flow`**. Where `superpowers-flow` wraps a single source (obra/superpowers), Engineering Flow keeps that proven spine (brainstorm → plan → TDD → debug → verify) and adds a best-of-breed code-review skill from compound-engineering plus a launch skill from agent-skills, so the full arc through review and shipping is covered from one Flow. `superpowers-flow` stays available and supported — install it instead if you want the single-source superpowers bundle.

## Attribution

The skills in `skills/` are not Flowy's work. They are vendored verbatim from their upstream authors:

- **Jesse Vincent / obra** — `brainstorming`, `writing-plans`, `test-driven-development`, `systematic-debugging`, `verification-before-completion` (from [obra/superpowers](https://github.com/obra/superpowers), MIT).
- **Every / EveryInc** — `ce-code-review` (from [EveryInc/compound-engineering-plugin](https://github.com/EveryInc/compound-engineering-plugin), MIT).
- **Addy Osmani** — `shipping-and-launch` (from [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills), MIT).

What Flowy added: the `FLOW.md` routing layer. Every vendored skill is MIT, so the Flow bundle as a whole is licensed **MIT**. See [ATTRIBUTION.md](./ATTRIBUTION.md) for per-skill author + license + source + SHA, and [LICENSE](./LICENSE) for the bundle license.

## How to use

Run `/flowy:engineering-flow` to activate. The Flowy hook then enforces FLOW.md routing for the rest of the session, with no manual setup. (`/flowy:engineering-flow status` to verify; `/flowy:engineering-flow deactivate` to turn off.)
