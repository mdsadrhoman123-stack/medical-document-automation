# 04 · Failure handling

The part of the system that took the longest to build and gets written about the least.

---

| What goes wrong | How it is detected | What the system does | Who finds out |
| :--- | :--- | :--- | :--- |
| **Extraction confidence is low** | Confidence gate | Flagged and routed to a human rather than passed on | Provider sees it flagged |
| **Scan is unreadable** | Extraction returns nothing usable | Held for manual handling, no partial output generated | Alert with the document reference |
| **AI provider call fails** | API error | Retried; the document stays queued rather than skipped | Alert if retries exhaust |
| **Worker dies mid-document** | Async queue | Task is retried from its record, not lost | Nobody if it recovers |
| **Output looks wrong to the clinician** | Sign-off gate | Rejected — nothing reaches the patient | The clinician decides |
| **Anything unanticipated** | Error handling on every stage | Halt before release, keep the record | Alert with the document reference |

## The three rules behind that table

**1 — Fail closed, not open.** When the system cannot establish that an action is safe, it holds. A held item is a visible problem. An item processed on a guess is an invisible one.

**2 — Nothing disappears.** Anything that cannot be completed is recorded where a human can find it later, not dropped from the run.

**3 — Silence is a fault.** An empty result where results were expected is treated as a possible failure of the source, not as an absence of work. This is the check most automations skip.

---

[← 03 · Architecture](03-architecture.md) · [05 · The stack →](05-stack.md)
