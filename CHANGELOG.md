# Changelog

## 1.2.0

- Automatic exclusion: the phrases "retrospectively registered" and "retrospective registration" no longer count as evidence of a retrospective study.
- Automatic exclusion: a record that describes itself as a randomised or clinical trial (and is not itself a review) is no longer excluded on a database label (PubMed publication type, Scopus or Web of Science document type), a MeSH term or retrospective wording in the abstract alone. It stays in the screening list.
- Automatic exclusion: random-allocation wording ("randomly assigned", "randomly allocated", "random assignment", "were randomised") now also marks a record as a trial, so a trial that calls itself a case-control or cohort study is not excluded on a MeSH term alone.
- Automatic exclusion: the label given by each database is now remembered per source. A PubMed publication type is trusted on its own (a PubMed "Comment" now goes to editorials, letters and errata). A Scopus or Web of Science "Review" label no longer excludes a record on its own as a narrative review: it needs a second database to agree and none to disagree (for example "Article" or a trial type), or review wording in the title or abstract. Otherwise the record stays in screening.
- The evidence column of the auto-excluded CSV names the database(s) behind a document-type exclusion.
- Deduplication rules are unchanged from 1.1.0.

## 1.1.0

- New rule: a trial registry record is flagged for review when its registration number (NCT, ISRCTN, ChiCTR, IRCT, ACTRN, DRKS, UMIN, JPRN, NTR, TCTR and similar) is cited in the text of another record, whatever the title similarity.
- In every flagged pair, the record with more information is shown as A and a trial registry record is always B, so "Same paper: remove B" keeps the full publication.
- When a record resembles several kept records, the best match (registry-number link first, then highest title similarity) is shown, instead of the first one found.
- Word-level highlighting of differing words in titles, authors and journals in the pair view.
- Research version only: adjudication drop-downs, accuracy summary with Wilson 95% intervals, accuracy summary CSV, nearest-record notes, and a note on flagged pairs kept by the reviewer.

## 1.0.0

- First public release: DOI, PMID and title matching; flagged pairs for review; RIS, PubMed, CSV, Web of Science and BibTeX input; optional exclusion of study types; PRISMA 2020 flow diagram (Word).
