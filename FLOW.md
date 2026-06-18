# FLOW.md: Engineering

> Routes a curated, cross-source set of engineering skills so the right one fires at each phase of building a feature: brainstorm the spec, write the plan, drive it with tests, debug failures at the root, review the diff, verify against reality, then ship safely.
> Skills vendored from obra/superpowers, EveryInc/compound-engineering, and addyosmani/agent-skills (all MIT) — see ATTRIBUTION.md. Routing by Flowy.

<!-- The Flowy engine supplies the universal contract (announce ritual, invoke/READ,
     host-wins, post-compaction re-read). This file carries only the routing. -->

## Phases

1. **Brainstorm** — entry: a new feature or behavior change, intent not yet pinned. Gate: intent + requirements explored, a spec agreed before any code.
2. **Plan** — entry: a spec exists, needs an ordered breakdown. Gate: a written, ordered implementation plan before code.
3. **TDD** — entry: a planned unit of work is ready to build. Gate: a failing (RED) test written and seen to fail before implementation; GREEN after.
4. **Debug** — entry: a test fails or behavior is unexpected. Gate: the root cause found from evidence before any fix lands.
5. **Review** — entry: a change is complete, before a PR. Gate: a structured persona review of the diff recorded.
6. **Verify** — entry: about to claim done / fixed / passing. Gate: the verification command run and its output confirmed before the claim.
7. **Ship** — entry: reviewed + verified, ready to deploy. Gate: a rollback path + monitoring in place before the deploy.

## Routing

```
USER MESSAGE RECEIVED
│
├─ INTAKE / TRIAGE  (always first)
│   └─ first message of a task, or a new request — classify intent before acting?
│       → invoke brainstorming
│       Gate: the intent named and the phase chosen before any edit
│
├─ DEBUG  (entry: something is broken / erroring / failing)
│   ├─ "a test fails" / "it throws" / "unexpected behavior"?
│   │   → invoke systematic-debugging
│   │   Gate: the root cause found from evidence before any fix is proposed
│   └─ "it regressed after my change"?
│       → invoke systematic-debugging
│       Gate: the regression reproduced and traced to a root cause first
│
├─ BRAINSTORM  (entry: new feature / behavior change, intent unpinned)
│   └─ "build X" / "add Y" / "change how Z works"?
│       → invoke brainstorming
│       Gate: intent + requirements explored, a spec agreed before code
│
├─ PLAN  (entry: a spec exists, needs ordered steps)
│   └─ "we have the spec — what's the approach / break it down"?
│       → invoke writing-plans
│       Gate: a written, ordered implementation plan before code
│
├─ TDD  (entry: a planned unit is ready to build)
│   ├─ "implement this feature"?
│   │   → invoke test-driven-development
│   │   Gate: a RED test written and seen to fail before implementation
│   └─ "fix this bug" (root cause already known)?
│       → invoke test-driven-development
│       Gate: a failing test that reproduces the bug before the fix
│
├─ REVIEW-LOOP  (entry: a change is complete, or feedback came back)
│   ├─ "review the diff before the PR"?
│   │   → invoke ce-code-review
│   │   Gate: a structured persona review of the diff recorded
│   └─ "re-review — feedback came back on the change"?
│       → invoke ce-code-review
│       Gate: each prior comment addressed and re-reviewed before re-claiming done
│
├─ DONE-CHECK / VERIFY  (before any "done" / "fixed" / "passing" claim)
│   └─ about to claim the work is done, fixed, or the tests pass?
│       → invoke verification-before-completion
│       Gate: the verification command run and its output confirmed before the claim
│
├─ SHIP  (entry: reviewed + verified, ready to deploy)
│   └─ "ship it" / "deploy to production"?
│       → invoke shipping-and-launch
│       Gate: a rollback path + monitoring in place before the deploy
│
├─ ADVISE-ONLY  (asking me to advise / explain, not to do the work)
│   └─ "should I…?" / "explain how X works"?
│       → answer only; do not start a phase
│       Gate: (soft) advice given; Routing: none
│
├─ SCOPE CHANGE  (the brief changed mid-stream)
│   └─ requirements changed after a spec or plan was set?
│       → re-enter brainstorming (then writing-plans) for the new scope
│       Gate: the new intent re-explored and the plan updated before more code
│
├─ BLOCKED  (waiting on an external dependency)
│   └─ cannot proceed until something external lands (API, review, deploy)?
│       → park; do not fake progress
│       Gate: the blocker named, the resume condition set
│
└─ DEFAULT / NO-MATCH  (always last)
    └─ nothing above fits this message?
        → answer only; ask one scoping question
        Gate: (soft) Routing: none — ask, do not guess
```

## Priority on collision

When more than one leaf could fire on the same message, resolve in this order:

1. **Debugging beats new work** — an active bug, failing test, or unexpected behavior routes to `systematic-debugging` BEFORE any new feature, plan, or fix. Find the root cause before proposing a change.
2. **Blocked / waiting on external** — surface a known blocker before starting new work; do not fake progress against an unavailable dependency.
3. **Scope changed** — a changed brief invalidates the open spec/plan; re-enter `brainstorming` → `writing-plans` before more code.
4. **Brainstorm before plan, plan before code** — on a fresh feature go `brainstorming` → `writing-plans` → `test-driven-development`; never skip to implementation with the spec or plan still open.
5. **RED before GREEN** — under `test-driven-development` the failing test is written and seen to fail before any implementation line.
6. **Verify before "done"** — `verification-before-completion` runs before any completion claim, commit message, or PR. Evidence precedes assertion.
7. **Review before ship, ship last** — `ce-code-review` precedes `shipping-and-launch`; the deploy phase is the tail of the arc, never the head.
8. **Advisory** — a pure "explain / should I" question answers without starting a phase.
9. **Default / no-match** — loses to everything; fires only when nothing else matches.

## You are rationalizing if you think…

- "Just code it, skip the brainstorm." → Brainstorm. A feature built on an unstated spec implements the wrong thing precisely.
- "The plan is obvious, skip writing it." → Plan. An unwritten plan drops a step under pressure; the order is the value.
- "I'll write the test after the code." → RED first. A test written after the fact tests what you built, not what you meant.
- "The bug is obvious, just patch it." → Debug. The obvious patch fixes the third symptom; trace to the one root cause first.
- "It looks done, ship it." → Verify. Run the command and read the output before the word "done" leaves your mouth.
- "I know which phase I am in after compaction." → Re-read this file and restate the phase before continuing.

## Attribution

- `brainstorming`, `writing-plans`, `test-driven-development`, `systematic-debugging`, `verification-before-completion` by **Jesse Vincent / obra** (https://github.com/obra/superpowers), MIT.
- `ce-code-review` by **Every / EveryInc** (https://github.com/EveryInc/compound-engineering-plugin), MIT.
- `shipping-and-launch` by **Addy Osmani** (https://github.com/addyosmani/agent-skills), MIT.
- FLOW.md routing by **Flowy**, MIT. Every vendored skill is MIT, so the Flow bundle as a whole is licensed MIT (see LICENSE + ATTRIBUTION.md).
