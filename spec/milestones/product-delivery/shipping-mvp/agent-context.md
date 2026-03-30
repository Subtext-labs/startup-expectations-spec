# Shipping your MVP

## Purpose

Turn a **scoped** MVP (see **defining-mvp-scope**) into **something in users’ hands** at an explicit **ship level**. This milestone is about **execution bar and learning**, not re-litigating strategy—strategy links through **relates_to** below.

## Outcomes (what “done” means)

| Id | Outcome | Why it matters |
|----|---------|----------------|
| **hypothesis-observable** | A real user can complete the **primary job** so you can see if the idea works | Without this, you shipped activity, not a test |
| **release-quality** | Quality matches the **level** you declared—no silent harm, honest gaps | Wrong bar either invalidates learning or burns trust |
| **learning-captured** | You know what to do next—continue, narrow, or stop | MVP is a loop, not a trophy |
| **pace-sustainable** | Another ship cycle is plausible without permanent crisis | Protects people and future velocity |

**Signals** for each outcome live in `goal.yaml` under `outcomes` for agents and validators.

## Levels (how good the release must be)

Levels are **not** seniority—they are **release rigor**: who may use the product and what failure modes you tolerate.

| Id | Label | Intent |
|----|-------|--------|
| **l0-internal** | Internal or dogfood | Prove build and integration; **not** market proof |
| **l1-private** | Private cohort | Learning-first; invited users; manual ops OK |
| **l2-limited** | Limited beta | Real daily use under caps; reliability and support matter |
| **l3-public-mvp** | Public MVP | Broad access; abuse, privacy, and ops must match exposure |

Each level has a **bar** (minimum quality) and **exit_criteria** in `goal.yaml`. Advance levels only when the **previous** level’s learning supports it.

## Outcomes × levels (matrix)

Use this to avoid “public launch” quality on a private beta, or “beta” excuses on a public URL.

| Outcome | l0-internal | l1-private | l2-limited | l3-public-mvp |
|---------|-------------|------------|------------|----------------|
| **hypothesis-observable** | Optional (often N/A for market) | Required for cohort | Required at cohort scale | Required at scale |
| **release-quality** | Team-safe | Cohort-safe | User-safe under load | Stranger-safe |
| **learning-captured** | Optional | Required | Required | Required |
| **pace-sustainable** | Required if you ship at all | Required | Required | Required |

## How this relates to other outcomes (cross-milestone)

- **customers** — A shipped MVP at **l1+** should produce **signals** you can take to **first-paying-users-design-partners**, **positioning-and-story**, or **feedback-loop-metrics**. No ship level guarantees revenue; it enables **evidence**.
- **funding** — Investors usually want **hypothesis-observable** + **learning-captured** tied to a narrative. **l0** rarely counts as traction; **l1–l2** often do for early stage if metrics are honest.
- **trust** — **l3-public-mvp** almost always drags **security-and-privacy-posture** and **incident-readiness** into scope. **l1** may still need basics if you handle sensitive data.
- **building** — **defining-mvp-scope** sets boundaries; **problem-solution-validation** sets what you are trying to learn; **shipping-mvp** is the **release act** and **bar**.

## Focus on

- One sharp hypothesis per ship; level-appropriate bar; documented gaps; learning fed forward.

## Worry less about

- Feature breadth, long-term scale proofs, or full GTM until this level’s outcomes are met.

## How this changes expectations

Engineering leadership: prioritize **release criteria**, **risk disclosure**, and **learning loops** over portfolio polish. Partner explicitly with product and customers milestones so the **same metrics** do not get reinterpreted after the fact.
