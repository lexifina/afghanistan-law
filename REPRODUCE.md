# How this repository was made (Afghanistan)

This file is written by the build on 2026-10-29, the day the source data was retrieved.

## Sources

| Source | Address | Retrieved | Licence |
| --- | --- | --- | --- |
| Ministry of Justice of Afghanistan, "Enforced Constitution of Afghanistan" | <https://moj.gov.af/en/enforced-constitution-afghanistan> | 2026-10-29 | No licence statement on the page; official publication of the ministry. |

Every word of law in this repository comes from these sources. Lexifina reads them and records each act's dated versions, and the laws that made each change, in one corpus file. This repository is built from that file.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `constitution` | Constitution of Afghanistan (2004) | 1 | 2004-01-03 to 2004-01-03 |

The build made 1 commits:

| Commits | Kind |
| ---: | --- |
| 1 | first version of an act |
| 0 | one law on its in-force day |
| 0 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `future`: laws not yet in force on 2026-10-29.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 0 laws in the record.
- 1 tags.

## Dates

Each commit is dated at noon (Asia/Kabul) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: Article 162 of the Constitution: it is enforced from the date of approval by the Loya Jirga, which its preamble gives as 3 January 2004. https://moj.gov.af/en/enforced-constitution-afghanistan

## How the history is built

`tools/build.py` turns the corpus into this history in one pass: one commit per law, on the day it took effect. The same corpus always gives the same commit hashes. `tools/check_repo.py` reads every version back from git and compares it with the corpus. `tools/on.py` shows the law as it stood on any date. The corpus format is described in `tools/SCHEMA.md`.

- Corpus: sha256 `586c861adfd9a0a0b3f9a800e6bf8fb0406400a25d2d0f0a7ac4cb3cef594d26` (86789 bytes).
- Builder blob hashes (`git hash-object`): `build.py` `6229396f41c9d7f1d6f405becfbe4097b35b82da`, `check.py` `5e112e6a33b7e93d00112e55f01fbb4fb3fdd8da`, `on.py` `644a6c0857fbcc72562032b58d57aa113fee0641`.
- Python 3.12.10; git version 2.46.0.windows.1.

## Checks

Not yet run for this build.

No second build of this corpus has been compared yet.

## Decisions made by hand

- Oldest version available: the ministry page shows one text and no history, so it is one version credited to the publisher, dated 3 January 2004, the Loya Jirga date given in the preamble and the date from which article 162 makes the Constitution enforced.
- The page heads article 53 "Articles 53"; it is read as Article 53.
- Typographic quotes and dashes were normalised; the wording is unchanged, including the page's typos.
- This is the text the ministry labels "Enforced". Whether and how it is applied today is a question of fact this record does not answer.

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- Claude Code wrote the deterministic parser; no model wrote or altered any legal text.
