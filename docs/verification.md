# Verification: what the numbers mean

The README claims 55, 47, 18, and a row of four zeros. This page turns those from assertions into receipts: what each battery tested, when it ran, and what stays private.

Method, common to all of it: every battery is a scripted run against the live system, not a mock. Implementation drafts and adversarial review were kept separate; every execution artifact went through a separate written review pass, over multiple rounds, before it was run. Each battery carries a safety strategy fitted to what it tests: boundary tests used isolated verification records with cleanup that is itself proven complete, hostile-state read tests ran inside rolled-back transactions, and seed promotion was atomic, rolling back every promotion if even one failed. The standing laws: no fabricated business data, ever; test-only state never survives a run; no manufactured staleness for demonstration purposes, ever.

The scripts, the schema, and the implementation are withheld. They are delivery work, and publishing the test suite would publish the design.

## Gate boundaries: 55 of 55, September 9, 2026

What the battery proved, by category:

- Direct writes to canonical storage are denied to the runtime identities, to a probe identity created for the test, and to the public role; canonical mutation happens only through the gate. A database administrator can of course alter a database; the proven boundary is the runtime and public surface.
- Proposal insertion is column-scoped: the application identity, which also holds read and evidence-intake capabilities, cannot supply workflow or audit fields, and forgery attempts are denied by the database, not by convention.
- Change records are server-derived from actual before-and-after state; a destructive request with an empty payload still produces an honest record of what died.
- The authenticated database actor is captured from the session, not from user input.
- Concurrent-edit protection: a proposal built against an outdated version is marked stale and refused rather than silently overwriting newer truth.
- Lifecycle rules hold: only live records can be updated, superseded, or retired; only non-live records can be restored; restoration does not resurrect retired relationships.
- Structural relationships retire automatically when a record is superseded or retired; historical relationships are append-only.
- Evidence citations must resolve to immutable document identifiers and survive document supersession; a record can prove which version it stood on even after that version was replaced.
- System-generated relationship types are rejected when a proposer tries to supply them by hand.
- Privilege hygiene: neither runtime identity is superuser, neither bypasses row security, and schema-level defaults were locked down and verified, not assumed.
- The battery checks itself: denial tests use otherwise-valid statements, probe setup is asserted, and cleanup completeness is proven so reruns are safe by test rather than by hope.

First run scored 53 of 55. The two failures were assertion-format bugs in the test script, not boundary breaches; they were reviewed, patched, and the rerun scored clean. That correction is part of the record on purpose.

## Seed integrity: 47 of 47, September 9, 2026

The initial truth went in through the same gate as everything after it, no bulk-import shortcut: 47 records proposed in one transaction, then 47 promotions in one transaction with a final assertion that rolls back every promotion if even one fails. The verdict required exact counts: 19 definitions, 28 canonical items, 7 evidence documents, 47 commits, zero pending, zero stale, zero rejected. Passed on the first run.

## Read surface: 18 of 18, September 14, 2026

- Grounded answers return class, dates, provenance, and class-specific detail; absent data returns as absence.
- Refusal fires on stale judgment-class records: proven with a positive control first, then denial cases, against the real database.
- Fail-closed behavior: a missing freshness policy, a malformed one, a non-numeric threshold, an absurdly oversized threshold, a null date, and a future date all produce a refusal state rather than an exception or a guess. All hostile-state tests ran rolled back.
- Credential separation: the promoting identity lost its raw read access when review found the original grant violated the intended boundary. The battery proves the denial both ways: gate identity cannot read, reading identity cannot promote.

## First value row: September 14, 2026, for the week ending September 11

Four weekly metrics, all zero, recorded as four separate observed facts through the same proposal-and-promotion path as everything else, with a scoped proof of 4 live values, 4 confirmed proposals, 4 commits. The zeros are part of the proof: the layer records the operating state it is given rather than improving the story.

## Infrastructure claims: audited September 15, 2026

A read-only audit script, itself reviewed before execution, checked the public security claims against the live machine and sorted every claim into verified, false, or unverifiable-from-inside. Public statements are limited to the verified list, worded as exactly what the commands proved. Known open items stay named as open rather than rounded up to done.

## What v0 does not prove

This is a first-party proof build, not a client production deployment. v0 does not prove multi-user authorization, client connector operation, client handover, or production operation with third-party corpus data. Those gates stay closed until a client requirement exists. The September 15 infrastructure review also left pre-client security work deliberately open; this repository does not present the build as security-complete.

## What remains private

The batteries, the schema, the gate implementation, the security configuration, the deployment recipe, and the extraction method. The counts above are public; the machinery is the engagement.
