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

## What was deliberately not used

- **A hosted automation SaaS.** Client data would transit a third party, and the failure handling would be limited to what that vendor exposes.
- **A bespoke application where automation was enough.** The cheapest system to maintain is the one with the least custom code in it.
- **Anything that could not be redeployed by someone else.** A system only one person can operate is a liability for the client.

---

[← 04 · Failure handling](04-failure-handling.md) · [06 · Results →](06-results.md)
