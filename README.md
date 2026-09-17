# The Owned Context Data Layer

**A business's canonical truth, on infrastructure the business controls.**

Definitions. Positioning. Decisions with their reasons. Evidence. The weekly numbers. One place, one owner, with dates, provenance, and evidence carried according to what each record actually is.

When a judgment-class record passes its shelf life, the layer refuses to ground answers on it until a human re-signs it. Operational records warn and stand. Decisions stay historical. Evidence stays evidence. The refusal is the feature.

> This repo is the concept and the proof. The build method is the paid work. Both statements are load-bearing.

---

## Why a separate layer

New AI tools land every week. Each one wants to hold your context for you, inside its own walls, on its own terms. String your business truth through enough tools and you become the context broker for your own company: re-explaining, re-uploading, re-correcting, forever.

The context data layer sits above the tools. Tools connect to it and read from it. When a tool dies or gets replaced, the truth doesn't move. It was never theirs.

## The loop

```
evidence informs → proposal → human gate → canonical record → answers with receipts
                                  ↑                                     |
                                  └──────── human re-signs ←── refusal when stale
```

Five laws hold it together:

1. **Nothing becomes truth without a named human approving it.** Tools and agents can propose. Only a person promotes.
2. **Every record carries the receipts appropriate to what it is.** Canonical records carry freshness and provenance. Decisions keep their dated history. Evidence keeps its source and document metadata. The layer does not invent fields a record does not have.
3. **Every canonical change through the gate is logged.** Who approved it, the authenticated database actor, and what actually changed are recorded. Prior state is preserved rather than silently overwritten.
4. **Freshness behavior is class-specific.** Owner-set thresholds act as trust backstops, not scheduled expiry. Past a threshold without revalidation, judgment-class records can refuse, operational records warn and stand, values go stale fast, and decisions remain historical.
5. **The credentials and access controls belong to the business.** Dedicated deployment the business controls, handed over at completion.

## Proof: mine runs

Built on my own company first, August 26 to September 14, 2026.

| What | Proof |
|---|---|
| Write-path boundaries (the gate) | 55-check battery, passed in full |
| Seeded canonical truth | 47 records, each through the gate with a named approver |
| Read surface (answers with receipts, refusals) | 18-check battery, passed on the first run |

## The receipts

This README makes the claims. The rest of the repo carries the evidence, which is how the product itself works:

- [docs/architecture.md](docs/architecture.md), the public shape of the system and the loop it runs
- [docs/verification.md](docs/verification.md), what the 55, 47, and 18 actually tested, when, and what stays private
- [docs/design-decisions.md](docs/design-decisions.md), seven decisions with rejected alternatives and costs, corrections included
- [CHANGELOG.md](CHANGELOG.md), the dated timeline of the build, mistakes on the record
- [examples/sample-output.md](examples/sample-output.md), what answers, refusals, and the brief look like, on invented data

## What is deliberately not here

The schema. The extraction method. The gate implementation. The security build. The delivery process. Those are the engagement, not the README.

If you're a founder or operator and this is the thing you've been trying to name: [CreativLabs.io](https://creativlabs.io).

Strategy first. Automation second. Sovereignty always.

---

*© 2026 CreativLabs.io. All rights reserved. Concept docs and sample outputs only; no implementation code is published here.*
