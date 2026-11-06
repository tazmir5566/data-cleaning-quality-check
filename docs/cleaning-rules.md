# Cleaning Rules

Rules applied to [`01-raw-sample-list.csv`](../data/01-raw-sample-list.csv) to produce [`02-cleaned-sample-list.csv`](../data/02-cleaned-sample-list.csv). Each change is recorded in [`03-issue-log.csv`](../data/03-issue-log.csv).

## Required fields

A record is **Ready** only when it has a company name, website, first and last name, job title and a correctly formatted email.

## Formatting rules

| Field | Rule |
| --- | --- |
| All text | Trim leading and trailing spaces |
| Names and titles | Standard capitalization (`sarah KIM` → `Sarah Kim`) |
| Company name | One spelling per company; drop punctuation variants (`Acme Analytics Inc`) |
| Website | Lowercase bare domain: no `http://`, `www.` or trailing slash |
| Email | Trim and lowercase. No other changes |
| City / state | Separate fields; state as a two-letter code |
| Country | Written in full: `United States` |

## Duplicates

- **Exact duplicate:** same person and same email after formatting → keep one record and list both original IDs in `source_record_ids`.
- **Same company, different person:** not a duplicate → keep both (R03 and R12).
- **Possible duplicate:** same name and company but a different email or title (R18 and R19) → keep both and mark **Needs review**. The list owner decides which one to use.

## Missing or invalid data

- An invalid email (for example a double `@`, a missing domain extension, or a space) is **cleared** and the record is marked **Needs research**. The likely correct address is not guessed, even when it looks obvious.
- A missing email, name or company is left blank and marked **Needs research**.
- A company is not inferred from a personal or free-mail style email domain (R16).
- Role-based addresses such as `procurement@` are kept but flagged, because they do not identify one decision-maker (R13).

## What this sample does not do

This sample checks format only. Checking whether an email is deliverable needs a verification tool, and no verification was run because the data is fictional.
