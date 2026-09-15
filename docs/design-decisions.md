# Design decisions

Seven decisions that define the system, each with what was rejected and what the choice costs. These are records, not slogans; several were corrected or narrowed under review, and where that happened it is said.

## 1. Evidence is not truth

**Decision:** Source documents live in their own corpus, and content versions are preserved across supersession. Canonical claims cite evidence by immutable identifier. Evidence is never refused for staleness and never treated as a claim.

**Rejected:** Treating the document pile itself as the knowledge base.

**Consequence:** A claim can prove which exact version of a document it stood on, even after that document was superseded. The cost is discipline: someone has to promote claims out of evidence deliberately, because the system will not do it for them.

## 2. One canonical write path, no exceptions for convenience

**Decision:** Nothing becomes truth except proposal, then human promotion, then commit. The initial seed of 47 records went through this path one record at a time, inside atomic transactions.

**Rejected:** A bulk-import shortcut for the initial seed. It would have been faster and would have created a class of records with weaker provenance than everything after them.

**Consequence:** Seeding was slower. Every canonical record born through the gate follows the same promotion and audit path, from the first day.

## 3. Stale judgment refuses instead of guessing

**Decision:** When a judgment-class record passes its freshness threshold without revalidation, the read surface declines to ground answers on it, visibly, until a human re-signs it.

**Rejected:** Warn-but-answer everywhere, which is friendlier and quietly trains the owner to ignore warnings.

**Consequence:** The system sometimes tells its owner no. That refusal is the trust mechanism: an answer that cannot be refused cannot be trusted either.

## 4. Freshness is class-specific, and it is a backstop, not a schedule

**Decision:** Thresholds differ by record class. Judgment canon can refuse. Operational records warn and stand. Observed values go stale within days. Dated decisions never go stale, because a decision is a historical fact.

**Rejected:** One global threshold, which was simpler and wrong twice over: too strict for history, too loose for weekly numbers.

**Consequence:** More policy to own. The thresholds were decided value by value by the owner, with a reviewer, and the policy itself lives in the layer as a gated record.

## 5. The promoting identity cannot read raw storage

**Decision:** The identity that promotes truth acts only through the gate functions. It holds no general read access.

**Rejected, after correction:** The original build granted the gate identity broad read access for convenience. Review flagged it as a violation of the intended boundary, the grant was revoked, and the removal was proven by test in both directions. This decision exists because a mistake was caught, and the record keeps it that way.

**Consequence:** Batch operations needed one narrow, purpose-built helper instead of general access. Slightly more machinery, one less quiet bypass.

## 6. Honest numbers or no numbers

**Decision:** Observed values enter only from real measurement, through the gate, with the measurement period recorded. The first weekly row was four zeros and each zero was recorded as its own observed fact, not explained away by a shared story. Manufactured staleness and demonstration theater are banned outright; a refusal is only ever shown if something is genuinely stale under the real policy.

**Rejected:** Fabricated starter values and manufactured demonstration staleness, both ruled out explicitly in review.

**Consequence:** Demonstrations are constrained by reality. Every retained production business value is an observed value, which is the only reason the numbers mean anything. Test-only state exists briefly inside rolled-back verification runs, by design, and never survives.

## 7. One business, one deployment, keys handed over

**Decision:** Each layer runs in a dedicated deployment the business controls, and completion means handing over the credentials and access controls.

**Rejected:** A multi-tenant platform, which scales better and reintroduces the exact dependency the layer exists to remove.

**Consequence:** Handover is the deployment, not an export button. The builder walks away without keys, which is the point, and the business takes on a named maintainer's duties, which are documented rather than hidden.
