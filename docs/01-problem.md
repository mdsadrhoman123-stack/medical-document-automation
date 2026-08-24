# 01 · The problem

**Medical Document Automation** — Longevity / hormone-optimization clinic (US)

---

A longevity and hormone-optimization clinic needed the document work behind patient care automated, without introducing the risk of an AI-generated error reaching a patient unreviewed.

In a medical context that is not an acceptable trade for speed. The constraint came first and the design followed it.

## Why it was not solved already

Every business in this position has already tried the obvious answers: a shared inbox, a spreadsheet, a rule in an off-the-shelf tool, a reminder to be more careful. Those work until volume grows or someone is on holiday.

The gap is not effort. It is that the process lives in people's habits rather than in a system, so it degrades quietly and nobody can measure by how much.

## What the requirement actually was

A 16-stage pipeline extracts text from PDFs and scans, structures it with an AI provider call, gates anything uncertain by confidence, and holds every output behind a mandatory provider sign-off before it can reach a patient.

---

[← README](../README.md) · [02 · The client journey →](02-journey.md)
