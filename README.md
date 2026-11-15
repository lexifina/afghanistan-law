# Afghanistan: law history in git


The law of Afghanistan as a git history: one file per provision, one commit per version on the day it took effect, and the act that made each change as the commit's author. `git blame` names the act behind every article; `git log` lists every change to an article; picking a date gives the text in force that day.

Part of [lexifina/global-law](https://github.com/lexifina/global-law), one git history for every country's law: this is Afghanistan's national law, which global-law reads at `afghanistan/national/acts/`.

**What is in it now:** the Constitution of Afghanistan (2004), in one version: the text the Ministry of Justice publishes as the "Enforced Constitution of Afghanistan", with its preamble, 12 chapter headings and 162 articles (175 files). No statute, decree or regulation is here yet. [`constitution/README.md`](constitution/README.md) lists every provision; [`REPRODUCE.md`](REPRODUCE.md) says how the files were made.

Each act is a folder with one file per provision: `constitution/art-034.md` is Article 34, `constitution/chapter-02.md` the heading of Chapter 2 and `constitution/preamble.md` the preamble.

The text is in English, as the Ministry of Justice publishes it. Its Dari and Pashto texts, the official languages under Article 16, are not part of this record.

## Questions as git commands

| Question | Command |
| --- | --- |
| Every change to Article 1 of the Constitution | `git log -p --word-diff -- constitution/art-001.md` |
| Which act wrote each line of Article 1? | `git blame constitution/art-001.md` |
| Every version of the Constitution, with the day each took effect | `git log --format="%h %(trailers:key=In-force,valueonly,separator=) %an" -- constitution ":^constitution/README.md"` |
| Article 1 as in force on 1 January 2026 | `python tools/on.py 2026-01-01 constitution art-001` |

**Outside git**, we also host this record publicly, for free:

- **[Ask Claude about Afghan law](https://global-law.lexifina.com/v1/try_claude?country=afghanistan)**: opens Claude with a first question ready.
- **[Ask ChatGPT](https://global-law.lexifina.com/v1/try_chatgpt?country=afghanistan)**: the same question in ChatGPT.
- **[Search Afghan law on our site](https://lexifina.com/law?country=afghanistan&q=freedom+of+expression)**: a search for "freedom of expression", with each provision's text and its versions, no account needed.
- **[Developer REST API](https://global-law.lexifina.com/v1/search_law?query=freedom+of+expression&jurisdiction=afghanistan)**: the same search as JSON, with no key. See the [documentation here](https://lexifina.com/api/global-law).

Both assistants read the record through the free Global law connector (MCP, `https://global-law.lexifina.com/mcp`); the first time, the chat gives you the link that adds it. Ask in English.

**Host it yourself easily.** All it takes is git and Python, and the tools run on your machine:

```sh
git clone --depth 1 https://github.com/lexifina/global-law && cd global-law
python3 tools/countries.py add afghanistan/national/acts
python3 tools/law.py show 2026-01-01 afghanistan/national/acts/constitution/art-001.md
```

Opened in Claude Code, Cursor, VS Code or Codex, the clone also starts a local MCP server with the same tools ([MCP.md](https://github.com/lexifina/global-law/blob/main/MCP.md)).

## Dates

Each commit is dated at noon, Asia/Kabul, on the day the version took effect, and carries it in its `In-force:` trailer:

- the one version is dated 3 January 2004, the day of the Loya Jirga's approval as the preamble gives it, from which Article 162 makes the Constitution enforced;
- the ministry's page states no amendment history, so no later version is recorded.

The version is credited to the publisher, the Ministry of Justice of Afghanistan, as the "oldest version available" (`Kind: publisher`), not to a law; the committer is Lexifina.

## How it is checked

- `tools/check_repo.py` reads every version back from git on the day it took effect and on the day before and compares it with the corpus, whose hash is in `data/corpus.sha256`; it also checks that every commit's trailers parse, that `main` has no merge commits and that no commit is dated in the future.
- `tools/build.py` writes the history from that one corpus file, and the same corpus gives the same commit hashes. [`REPRODUCE.md`](REPRODUCE.md) records that the checks were not yet run for this build and that no second build has been compared.
- The sha256 of the page bytes the text was parsed from is in `data/versions.json`. Quotes and dashes are normalised; the wording is the page's own, typos included.

## What it does not show

- **Amendments.** The ministry's page shows one text and no history, so nothing here records a change before or after it.
- **Statutes, decrees and regulations.** None yet.
- **Earlier constitutions**, which are not versions of the 2004 text.
- **How the text is applied.** The record holds what the ministry publishes as the enforced text, not whether or how it is applied in practice.

## Sources

| Source | Kind | Past versions | Notes |
| --- | --- | --- | --- |
| [Ministry of Justice of Afghanistan](https://moj.gov.af/en/enforced-constitution-afghanistan) | Official publication: "Enforced Constitution of Afghanistan" | no, one text | Read on 29 October 2026; the page states no amendment history |

## Licence

See [`LICENSE`](LICENSE). The ministry's page carries no licence or copyright statement; the text is reproduced as an official publication of the ministry, with attribution to it. Lexifina's arrangement, tables, commit messages and tools may be reused under CC BY 4.0.

No AI model wrote, translated or corrected legal text; the scripts were written by an AI model (see [`REPRODUCE.md`](REPRODUCE.md)).

## More

From [lexifina/global-law](https://github.com/lexifina/global-law):

- [FEATURES.md](https://github.com/lexifina/global-law/blob/main/FEATURES.md): every feature, and what every corpus must support (`git blame`, `law.py`, the MCP tools)
- [FAQ.md](https://github.com/lexifina/global-law/blob/main/FAQ.md): questions and answers · [CONTRIBUTING.md](https://github.com/lexifina/global-law/blob/main/CONTRIBUTING.md): proposing changes · [MCP.md](https://github.com/lexifina/global-law/blob/main/MCP.md): the MCP server · [REPRODUCE.md](https://github.com/lexifina/global-law/blob/main/REPRODUCE.md): how it was built · [CHANGELOG.md](https://github.com/lexifina/global-law/blob/main/CHANGELOG.md)
- [FRESHNESS.md](https://github.com/lexifina/global-law/blob/main/FRESHNESS.md): how current each corpus is · [Monitoring](https://github.com/lexifina/global-law/tree/main/monitoring): whether updates are running · [WATCHING.md](https://github.com/lexifina/global-law/blob/main/WATCHING.md): how each official source is watched for changes
- [performance/](https://github.com/lexifina/global-law/tree/main/performance): how fast the tools are, measured
- [visualisations/](https://github.com/lexifina/global-law/tree/main/visualisations): charts and bridges across the world's law
- [Vulnerabilities](https://github.com/lexifina/global-law/tree/main/vulnerabilities): mistakes in legislation as published
