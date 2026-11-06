# Data Cleaning and Quality Check

A demonstration of how a messy contact list is turned into a consistent, usable file, with every change documented.

> **Synthetic data notice:** All companies, people, websites and emails here are fictional and use the reserved `.example` top-level domain. This is a demonstration project, not paid client work.

## Before and after

| | Count |
| --- | --- |
| Records in the raw file | 20 |
| Exact duplicates removed | 2 |
| Records in the cleaned file | 18 |
| — Ready to use | 10 |
| — Needs research (missing or invalid data) | 6 |
| — Needs review (possible duplicate, client decision) | 2 |
| Issues logged | 16 |

## Files

| Step | File | What it shows |
| --- | --- | --- |
| 1 | [`data/01-raw-sample-list.csv`](data/01-raw-sample-list.csv) | The original list with deliberate problems |
| 2 | [`data/02-cleaned-sample-list.csv`](data/02-cleaned-sample-list.csv) | The cleaned list, with `source_record_ids`, `qa_status` and `qa_notes` columns |
| 3 | [`data/03-issue-log.csv`](data/03-issue-log.csv) | Each issue found, the records affected and the action taken |
| — | [`docs/cleaning-rules.md`](docs/cleaning-rules.md) | The rules applied and how unclear cases were handled |

## Issues covered

- Duplicate records
- Inconsistent company names (`ACME ANALYTICS INC.` vs `Acme Analytics, Inc`)
- Extra whitespace and inconsistent capitalization
- Mixed website and location formats
- Missing required fields
- Invalid email formats

## Main principle

Cleaning fixes format, not facts. Missing or broken details are flagged for research rather than filled in by guesswork, and records that may or may not be duplicates are kept and marked for the client to decide. Every cleaned record can be traced back to its original row.

---

Prepared by [Tazmir Hossain](https://github.com/tazmir5566) · B2B Lead Warriors
