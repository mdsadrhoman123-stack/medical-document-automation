# 07 · Limitations

Written by the person who made the trade-offs.

---

- The sign-off gate is intentionally a bottleneck. Throughput is bounded by clinician review time, which is the correct trade in a medical setting.

- The confidence gate reduces the chance of an unnoticed error; it does not eliminate it. That is why sign-off is mandatory rather than conditional.

- Reference handling is specific to this clinic's protocols. Another practice would need its own configuration, not a copy.

## On reading this section

A limitations section is not a disclaimer. It is the fastest way to tell whether a system was designed or assembled. Every one of the constraints above was a decision with a reason behind it, and each one could be lifted — at a cost that was not worth paying for the problem in this brief.

If your situation makes a different trade the right one, that is a conversation worth having.

---

[← 06 · Results](06-results.md) · [README](../README.md)
