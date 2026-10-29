# Afghanistan: law history in git

The law of Afghanistan as a git history: one file per provision, one commit per law on the day its change took effect, and the law that made each change as the commit's author. `git blame` names the law behind every line; picking a date gives the text in force that day.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law), which places it at `af/`.

**What is in it now**

| Folder | Law | Versions | History |
| --- | --- | ---: | --- |
| `constitution/` | Constitution of Afghanistan (2004), as published by the Ministry of Justice under the title "Enforced Constitution of Afghanistan" | 1 | Oldest version available, dated 3 January 2004. Files: `preamble`, `chapter-NN` (the 12 chapter headings) and `art-NNN` (articles 1 to 162) |

**Language.** English, as the Ministry of Justice publishes it (the ministry also publishes Dari and Pashto pages).

**Limits of this first build**

- One version, credited to the publisher as "oldest version available". The ministry page shows no amendment history, so there is no history before or after it.
- The date is the Loya Jirga date in the preamble, from which article 162 makes the Constitution enforced.
- The record says what the ministry publishes as the enforced text. It does not say how that text is applied in practice.
- Statutes and decrees are not included.

**Source.** Ministry of Justice of Afghanistan, [moj.gov.af/en/enforced-constitution-afghanistan](https://moj.gov.af/en/enforced-constitution-afghanistan), read on 29 October 2026. The sha256 of the bytes it was parsed from is in `data/versions.json`.

How these files were made is in [REPRODUCE.md](REPRODUCE.md). This repository is not legal advice and not an official publication; for anything that matters, read the original.
