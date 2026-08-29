# 05 · The stack

Each choice, and the reason for it.

---

| Component | Why this one |
| :--- | :--- |
| **FastAPI** | Service layer for the pipeline |
| **Claude via AWS Bedrock** | Document structuring inside the client's AWS account |
| **Textract** | Extraction from scans |
| **pdfplumber** | Extraction from text-layer PDFs |
| **python-docx** | Generates the structured output document |
| **PostgreSQL on RDS** | Managed, backed-up record store |
| **Celery / Redis** | Async processing that survives a restart |
| **S3** | File storage |

## The decisions behind that table

### Why sign-off is mandatory rather than conditional on confidence

**What it does.** Every output waits for a provider signature, no matter how confident the pipeline was about it.

**What was turned down.** Releasing automatically above a confidence score. That is where nearly all the throughput is — and a confidence gate only catches the errors it can see, and the dangerous ones in a clinical document are the confident ones.

**What that costs.** Throughput is bounded by clinician review time. In a medical setting that is the correct trade, and it means the system cannot be sold on speed.

### Why there are two extractors instead of one

**What it does.** Text-layer PDFs go through pdfplumber; scans go to Textract. The document decides which.

**What was turned down.** OCR for everything. One path to maintain and one failure mode — and it re-recognises text that was already perfect, inventing errors in documents that had none.

**What that costs.** A routing decision before extraction, and two failure modes to design for rather than one.

### Why the AI call runs inside the client's own AWS account

**What it does.** Document structuring goes through Bedrock in the client's account, so the documents never leave their boundary.

**What was turned down.** Calling the provider API directly. Simpler credentials and one less service to configure — and patient documents then cross into infrastructure the clinic has no agreement with.

**What that costs.** Tied to what Bedrock offers in that region. Reference handling is also specific to this clinic's protocols, so another practice needs its own configuration rather than a copy of this one.

## The rule that applies to all of them

**Nothing that only one person can operate.** A system that depends on the engineer who built it is a liability for the client, however well it runs on the day it is handed over. Every choice above had to survive that test before the technical merits mattered at all.

---

[← 04 · Failure handling](04-failure-handling.md) · [06 · Results →](06-results.md)
