# What the layer sounds like

Sample outputs from a context data layer, using an invented company (Meridian Freight Advisory) and invented data. Illustrative output based on live behavior; labels and field names are simplified, and every value below is fiction.

## 1. Ask it a question, get receipts

Query: `search "pricing"`

```
class      | record                          | record date | state
-----------+---------------------------------+-------------+-----------
DEFINITION | qualified opportunity           | 2026-07-02  | FRESH
CANON      | engagement pricing floor        | 2026-08-19  | FRESH
DECISION   | 2026-06-11 dropped hourly rates | 2026-06-11  | HISTORICAL
EVIDENCE   | rate card v3 (doc, immutable)   | 2026-05-30  | EVIDENCE
```

Each row says what kind of record it is and carries the dating and provenance appropriate to that class. Canonical freshness appears where it applies. Decisions remain historical. Evidence remains evidence. When superseded, a decision keeps its original date and remains historical while retained; decisions don't rot, they get superseded by newer decisions, with receipts pointing back.

## 2. Watch it refuse

Query: `grounds "discount policy"`

```
ground_state    | record                  | record date | note
----------------+-------------------------+-------------+----------------------------------
REFUSED_STALE   | discount approval rule  | 2026-01-15  | judgment-class, 243 days unsigned
GROUND          | rate card v3 (evidence) | 2026-05-30  | evidence stands; not judgment
```

The discount rule went 243 days without a human re-signing it. So the layer will not ground an answer on it. No confident guess, no silent fallback. It names the record, names the age, and waits for a person.

## 3. The layer speaks first

Twice a week, on a schedule, the layer writes its owner a brief without being asked:

```
Meridian context layer - brief for 2026-09-14
----------------------------------------------
policy      | freshness thresholds live for all record classes
attention   | 1 record refusing: discount approval rule (unsigned 243 days)
pending     | 0 proposals waiting at the gate
evidence    | 12 documents live, newest ingested 2026-09-02
numbers     | week ending 2026-09-11: outreach 6, replies 2, calls held 1, proposals 1
```

The brief makes drift visible without waiting for someone to remember to look.

---

*All names and values invented. Illustrative of a live layer's behavior; labels and field names simplified.*
