# FLOW.md: Engineering

> Routes a curated set of engineering skills so the right one fires at each phase of building a feature: brainstorm the spec, write the plan, drive it with tests, debug failures at the root, review the diff, verify, and ship it safely.
> Skills vendored from obra/superpowers, EveryInc/compound-engineering, and addyosmani/agent-skills (all MIT) — see ATTRIBUTION.md. Routing by Flowy.

<!-- The Flowy engine supplies the universal contract (announce ritual, invoke/READ,
     host-wins, post-compaction re-read). This file carries only the routing. -->

## Routing

```
USER MESSAGE
  ├─ new feature / behavior change — explore intent first?   → invoke brainstorming                   gate: spec agreed before code
  ├─ have a spec — break it into ordered steps?              → invoke writing-plans                    gate: written plan before code
  ├─ implementing a feature or bugfix?                       → invoke test-driven-development           gate: RED test before implementation
  ├─ a test fails / a bug / unexpected behavior?             → invoke systematic-debugging             (precedes any fix)
  ├─ finished a change — review the diff before a PR?        → invoke ce-code-review
  ├─ about to claim "done" / "fixed" / "passing"?            → invoke verification-before-completion    gate: evidence before the success claim
  ├─ ready to deploy to production?                          → invoke shipping-and-launch              gate: rollback + monitoring planned
  └─ question, not engineering work?                          → answer only; no skill
```

## Priority on collision

When more than one branch matches, resolve top-down:

1. **Debugging beats new work**: an active bug, failing test, or unexpected behavior routes to `systematic-debugging` BEFORE any new feature, plan, or fix — find the root cause before proposing a change.
2. **Brainstorm before plan, plan before code**: on a fresh feature go `brainstorming` → `writing-plans` → `test-driven-development`; never skip to implementation with the spec or plan still open.
3. **RED before GREEN**: under `test-driven-development` the failing test is written and seen to fail before any implementation line.
4. **Verify before "done"**: `verification-before-completion` runs before any completion claim, commit message, or PR — evidence precedes assertion.
5. **Review before ship, ship last**: `ce-code-review` precedes `shipping-and-launch`; the deploy phase is the tail of the arc, never the head.

## Phases

1. **Brainstorm**: brainstorming. Gate: intent + requirements explored, a spec agreed before any code.
2. **Plan**: writing-plans. Gate: a written, ordered implementation plan.
3. **TDD**: test-driven-development. Gate: a failing (RED) test before implementation, GREEN after.
4. **Debug**: systematic-debugging. Runs on any bug / failure; root cause found before a fix lands.
5. **Review**: ce-code-review. Structured persona review of the diff before a PR.
6. **Verify**: verification-before-completion. Gate: verification commands run + output confirmed before claiming done.
7. **Ship**: shipping-and-launch. Gate: rollback strategy + monitoring in place before deploy.

**Shortcut:** quick bugfix → systematic-debugging → test-driven-development → verification-before-completion (skip brainstorm/plan).

## Attribution

- `brainstorming`, `writing-plans`, `test-driven-development`, `systematic-debugging`, `verification-before-completion` by **Jesse Vincent / obra** (https://github.com/obra/superpowers), MIT.
- `ce-code-review` by **Every / EveryInc** (https://github.com/EveryInc/compound-engineering-plugin), MIT.
- `shipping-and-launch` by **Addy Osmani** (https://github.com/addyosmani/agent-skills), MIT.
- FLOW.md routing by **Flowy**, CC-BY-SA-4.0. Every vendored skill is MIT, so the Flow bundle as a whole is licensed MIT; see LICENSE + ATTRIBUTION.md.
