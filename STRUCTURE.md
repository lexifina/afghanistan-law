# Structure

The law of record is the text the Official Gazette of Afghanistan (جریدۀ رسمی) prints. The gazette prints every
instrument in Pashto and Dari; this repository holds the Dari text. Folders are named in Dari, by type of
instrument, then by the solar-hijri year of the gazette, then by gazette number and title:

| Folder | What it holds |
| --- | --- |
| `قانون-اساسی/<year>-<title>/` | The Constitution |
| `قوانین/<year>/<gazette>-<title>/` | Laws (قانون) and codes (کود), and the instruments that amend them |
| `فرامین-تقنینی/<year>/<gazette>-<title>/` | Legislative decrees (فرمان تقنینی) |
| `فرامین/<year>/<gazette>-<title>/` | Decrees (فرمان) |
| `مقررات/<year>/<gazette>-<title>/` | Regulations (مقرره) |
| `اساسنامه-ها/`, `طرزالعمل-ها/`, `لوایح/`, `اصولنامه-ها/`, `مصوبات/` | Statutes of public bodies, procedures, by-laws, older laws (اصولنامه), resolutions |
| `معاهدات/<year>/<gazette>-<title>/` | Treaties and agreements the gazette publishes |
| `سایر-اسناد/<year>/<gazette>-<title>/` | Other instruments |
| `translations/en/` | English translations: the Ministry of Justice's English Constitution of 2004 |

e.g. `قوانین/1393/1132-قانون-اجراآت-جزائی/ماده-382.md` is article 382 of the Criminal Procedure Code, published
in gazette No. 1132 of 15 Saur 1393. Each act folder holds one file per article (`ماده-001.md`) and a
`README.md` with the gazette number and date, the source file and the article list. No folder holds more than
1,000 entries. Notices (اعلانات), trademark lists and other non-legislative items are not taken.

Each instrument is one commit as the gazette publishes it (as enacted). An instrument that amends another is
its own folder; the amended text is not consolidated here.

## Dates

Each version is one commit, dated 12:00 Asia/Kabul on the day it took effect, which its `In-force:` trailer
repeats. `In-force-basis:` gives the rule and quotes the instrument's own commencement article:

- `publication`: in force from publication in the gazette; the date is the gazette's;
- `one-month-after-publication` / `N-days-after-publication`: counted from the gazette's date;
- `publication-as-at`: effective from signing or approval, a day the gazette entry does not give; dated the day
  the gazette was published, by which it was in force at the latest.

An instrument whose commencement article the builder cannot read is held, not guessed. The gazette date is the
solar-hijri date the ministry's database gives (for gazettes it dates by the lunar calendar, the solar date in
the gazette's own running head), converted to the Gregorian calendar. No date in this repository is the day we
downloaded anything.

## Authority

The `Authority:` trailer names the state as it was when the gazette was published: the Islamic Republic of
Afghanistan (2004 to 15 August 2021), and from 15 August 2021 the de facto authorities as the gazette names them
(Islamic Emirate of Afghanistan). It records who published the instrument, not a view on its validity.

## Text

The Dari text is the gazette PDF's own text layer, as the ministry publishes it; nothing is OCRed. The layer is
normalised mechanically (Unicode presentation forms, justification stretch, digit runs and brackets stored in
visual order); no word is corrected, so the layer's own errors, such as spaces inside words, remain.

Many gazettes are set in the legacy font Pashto Aryob, embedded with a shifted ToUnicode table, so their text
layer reads as other letters although the page prints correctly. For these (`Text-source: legacy-font
conversion`) each glyph's character is taken from the code the embedded font itself assigns that glyph (Unicode
Arabic presentation forms, by their standard decomposition; the font's private-use codes for Pashto letters by
the value the font's correct subsets give them), and lines are rebuilt from glyph positions. No image is read.
The conversion agrees glyph for glyph with the publisher's own table wherever that table is correct, and it was
checked against text the same gazettes print with a correct table (REPRODUCE.md).
