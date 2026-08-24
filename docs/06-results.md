# 06 · Results

---

## Counted

| | |
| :--- | :--- |
| Pipeline stages | **16** |
| Mandatory sign-off gates | **1** |
| Unreviewed patient outputs | **0** |

These are counts from the built system: nodes, stages, versions, gates, retries. They are verifiable from the workflow itself.

## What changed in the process

| | Before | After |
| :--- | :--- | :--- |
| **Document turnaround** | Clinician hours of data entry | Automated draft, clinician reviews |
| **Uncertain extraction** | Indistinguishable from certain | Flagged by a confidence gate |
| **Patient-facing output** | Whatever was typed | Nothing without provider sign-off |
| **Where data sits** | Ad hoc | Client's own AWS account |
| **Failed processing** | Silently missing | Queued and retried, or alerted |

## What is deliberately not claimed

No time-saved percentage, cost-reduction figure or throughput multiplier appears in this repository. Those numbers require a measured baseline and a measured after, over a stated period, on a stated definition. Where that measurement exists it will be published with its method. Where it does not, the number is not worth more than the process description above.

> An unsourced percentage in a portfolio is a claim the reader has to take on trust. A node count is a claim they can check.

---

[← 05 · The stack](05-stack.md) · [07 · Limitations →](07-limitations.md)
