# startup-expectations-spec

Open specification (Apache 2.0) for **what “good” looks like** across roles and situations—written so **founders and operators** can browse it without HR jargon. Contributions welcome. See [LICENSE](LICENSE).

## How this spec is organized

| Idea | In plain language | Example |
|------|-------------------|---------|
| **Industry** | Broad type of company | Tech, healthcare, finance — see [`spec/industries/`](spec/industries/) |
| **Segment** | Who you sell to or how you operate | e.g. [enterprise SaaS](spec/industries/technology/segments/enterprise-saas/) |
| **Role** | The job you are asking about | Engineering manager, first designer — under segment [`roles/`](spec/industries/technology/segments/enterprise-saas/roles/) |
| **Responsibilities** | What strong performance looks like in that context | Written in [shared](spec/shared/roles/) + company-specific layers |
| **Milestone** | A big moment you are working toward | Raising a seed, shipping an MVP, first hire — see [`spec/goals/`](spec/goals/) |
| **Maturity** | How much proof the company has (stage) | Pre-seed → seed → Series A — see [`spec/maturity/`](spec/maturity/) |

Same job title can mean different things in different contexts—the **folder path** shows which situation you mean.

## Maturity-first lists (pre-seed, seed, Series A)

If **stage** is what you care about most, start here—ordered tables that link to each milestone’s **`checklist.md`**:

- [Pre-seed](spec/maturity/pre-seed.md)
- [Seed](spec/maturity/seed.md)
- [Series A](spec/maturity/series-a.md)

Hub and machine index: [spec/maturity/README.md](spec/maturity/README.md), [spec/maturity/index.yaml](spec/maturity/index.yaml).

## Milestone categories (one main focus each)

Each milestone sits in one bucket so lists stay simple:

| Category | Folder | What it covers | Example milestones |
|----------|--------|----------------|----------------------|
| **Fundraising & runway** | [`goals/funding/`](spec/goals/funding/) | Money, runway, investors, how you use a round | Raising a seed round |
| **Build & ship** | [`goals/building/`](spec/goals/building/) | What you build, launch, and ship as product and systems | Shipping your MVP, technical foundation |
| **Customers & revenue** | [`goals/customers/`](spec/goals/customers/) | Who buys, how you reach them, pricing, narrative, revenue signals | Early GTM motion, first case studies |
| **Trust, compliance & risk** | [`goals/trust/`](spec/goals/trust/) | Security, privacy, rules, integrity, IP—can you sell and operate safely? | SOC 2 path, incident readiness |
| **Operations & back office** | [`goals/operations/`](spec/goals/operations/) | Finance rhythm, payroll, contracts, insurance—how the company runs | Company financial backbone, cap table hygiene |
| **Hiring & team** | [`goals/team/`](spec/goals/team/) | Who you hire and how they start | Hiring your first developer |

If two things apply (e.g. hiring after a raise), use the bucket that matches the **main** question—**team** for hiring steps, **funding** for raising and investor narrative, **operations** for payroll and vendor contracts, **customers** for “how we grow revenue,” **trust** for “can we pass security review.”

**Full milestone list** — [spec/goals/milestone-catalog.md](spec/goals/milestone-catalog.md). The registry is [spec/goals/_registry.yaml](spec/goals/_registry.yaml). Flat search index: [spec/milestone-index.yaml](spec/milestone-index.yaml).

## What each milestone folder contains

Paths look like `spec/goals/<category>/<milestone-id>/` (example: [shipping-mvp](spec/goals/building/shipping-mvp/)).

- **`goal.yaml`**: Short title, `category`, `tags`, and an **`agent_hint`** (one line for tools). **`load`** lists files to read in order. Some goals also define optional **`outcomes`**, **`levels`**, and **`relates_to`** (see [goal.schema.json](spec/schema/goal.schema.json)).
- **`agent-context.md`**: What to prioritize, what to deprioritize, and how expectations shift for this milestone—no duplicate of full role docs.
- **`checklist.md`**: Actionable tick list (same folder; also listed in [milestone-index.yaml](spec/milestone-index.yaml)).

Milestones **frame** role specs; they do not replace them.

## For assistants and tools

1. Start at [spec/manifest.yaml](spec/manifest.yaml) (schemas, registries, read order).
2. For stage-ordered work, open [spec/maturity/index.yaml](spec/maturity/index.yaml) or the [maturity](spec/maturity/) Markdown lists.
3. Open [spec/goals/_registry.yaml](spec/goals/_registry.yaml) for categories and milestone paths.
4. Open each `spec/goals/<category>/<milestone-id>/goal.yaml`, then follow **`load`** in order (paths are under `spec/`).
5. For roles, merge **`extends`** in `role.yaml` then the leaf **`responsibilities.md`** as described below.

## Shared vs company-specific expectations

**Shared:** [`spec/shared/roles/<role-id>/`](spec/shared/roles/) (`responsibilities.md`) — baseline that often applies across industries. Registry: [spec/shared/roles/_registry.yaml](spec/shared/roles/_registry.yaml).

**Company-specific:** [`spec/industries/.../roles/<role-id>/`](spec/industries/) — only what changes for that industry or segment.

Read **shared first, then the leaf**. `role.yaml` can list **`extends`** for shared files. Example leaf: [engineering-manager role](spec/industries/technology/segments/enterprise-saas/roles/engineering-manager/) (see [`role.yaml`](spec/industries/technology/segments/enterprise-saas/roles/engineering-manager/role.yaml)).

## Repository layout

```
spec/
  manifest.yaml
  maturity/
    README.md
    index.yaml
    pre-seed.md
    seed.md
    series-a.md
  schema/
    role.schema.json
    goal.schema.json
  goals/
    _registry.yaml
    milestone-catalog.md
    <category>/
      meta.yaml
      <milestone-id>/
        goal.yaml
        agent-context.md
        checklist.md
  shared/
    roles/
      _registry.yaml
      <role-id>/
        responsibilities.md
  industries/
    _registry.yaml
    <industry-id>/
      meta.yaml
      segments/
        _registry.yaml
        <segment-id>/
          meta.yaml
          roles/
            <role-id>/
              role.yaml
              responsibilities.md
```

**Quick links:** [spec/](spec/) · [spec/manifest.yaml](spec/manifest.yaml) · [spec/schema/](spec/schema/) · [spec/goals/](spec/goals/) · [spec/maturity/](spec/maturity/) · [spec/shared/](spec/shared/) · [spec/industries/](spec/industries/)

- **`meta.yaml`**: Human title and short summary for an industry, segment, or milestone category.
- **`_registry.yaml`**: Lists children so tools and reviewers can validate the tree.
- **`role.yaml`**: stable `id`, display `title`, `version`, optional `extends`, leaf responsibilities file. Schemas: [role.schema.json](spec/schema/role.schema.json), [goal.schema.json](spec/schema/goal.schema.json).
- **`manifest.yaml`**: Entry point for tools.

## Contributing

Change [`spec/industries/`](spec/industries/) via pull request; one logical change per PR when possible. Bump **`version`** on `role.yaml` when expectations meaningfully change. New milestones: add under `spec/goals/<funding|building|customers|trust|operations|team>/<milestone-id>/`, set **`category`**, register in [spec/goals/_registry.yaml](spec/goals/_registry.yaml) and [spec/milestone-index.yaml](spec/milestone-index.yaml), and keep **`load`** lists explicit.
