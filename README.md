# Telic Labs

**Original software engineering tasks for training and evaluating coding agents.**

Telic Labs authors multi-file software engineering tasks and delivers them as reproducible containerised environments. Every task ships with the evidence that establishes its difficulty, so the number can be checked rather than taken on trust.

---

## The problem we build against

A coding agent that fails a task at 0% tells you one of four things: the task is genuinely hard, the specification is under-determined, the environment is broken, or the verifier rejects correct solutions. From the outside these are indistinguishable, and in practice the last three are common.

The public record bears this out. In February 2026 OpenAI retired SWE-bench Verified after auditing 138 problems its models consistently failed and finding that 59.4% contained material defects in test design or problem description. Independent audits of other coding benchmarks have measured verifiers accepting incorrect implementations and rejecting correct ones at double-digit rates.

Writing a hard problem is straightforward. Demonstrating that the grader is correct is not. We treat the second problem as the product.

---

## What a task package contains

```
task-<id>/
├── instruction.md        # the only text the agent sees
├── environment/          # Dockerfile, pinned digests, vendored deps, seed repo
├── verifier/             # spec, regression and anti-hack tiers; grading rules
├── solution/             # reference implementation, rationale, oracle run
├── evidence/             # rollouts, difficulty profile, verifier audit, blind solve
└── provenance/           # authorship record, originality attestation, canary
```

The `evidence/` directory is the part most vendors do not ship. It contains the raw agent trajectories behind the difficulty figure, with model versions, scaffolds, seeds, token counts and wall-clock, so a reviewer can recompute every number themselves.

---

## What we commit to, per task

| Property | Commitment |
|---|---|
| Originality | Authored to order. Never published anywhere. Screened against public corpora and canaried. |
| Oracle stability | Reference solution passes 10/10 independent instantiations across two host architectures |
| Flaky tests | Zero, across 20 runs on unchanged code |
| Verifier false-accept rate | Measured and published per task |
| Verifier false-reject rate | Measured and published per task |
| Human feasibility | An independent engineer solves it blind from the specification alone |
| Reward-hacking resistance | Full adversarial checklist attempted; the attempt log ships with the task |
| Difficulty | Measured across multiple model families and scaffolds, with confidence intervals |
| Offline build | Image builds and tests run with network egress denied |
| Failure triage | Every failure classified against a fixed taxonomy by someone who did not author the task |

Tasks that fail a hard gate are not delivered and are not billed.

---

## How we think about difficulty

Agent failure is a hypothesis to be disproven, not a result to be celebrated. A task is only described as hard once specification defects, verifier defects, environment defects and harness artefacts have been ruled out by reading the actual trajectories.

For reinforcement learning this matters commercially as well as intellectually. A task with a 0% pass rate produces no learning signal, and a verifier that accepts a wrong answer teaches a model that the wrong answer is right. We measure both.

---

## Who this is for

- **Frontier AI labs** building or evaluating coding agents
- **Data providers** holding lab contracts that require verified environments rather than labelled examples
- **Independent evaluators** who need held-out task sets they did not author themselves

---

## Status

Telic Labs is early stage and building deliberately. We are taking a small number of design partners rather than scaling volume ahead of quality.

We begin every engagement the same way: three complete tasks, built to our full standard with the entire evidence package, at no charge. It is the fastest way to establish whether our definition of a good task matches yours.

---

## Contact

**Vishwastam Shukla** — Founder
vishwastam.shukla@gmail.com · [LinkedIn](https://linkedin.com/in/vishwastam-shukla) · Bangalore, India

Our full standard operating procedure — twelve production stages, nine gates, the failure taxonomy and the adversarial hardening checklist — is available to prospective partners under NDA.
