# Changelog

## 1.2.3

- Automatic exclusion: a database label on its own no longer excludes a record. An exclusion based on a PubMed publication type, a Scopus or Web of Science document type, or a MeSH term (case reports, systematic reviews, narrative reviews, editorials and letters, retrospective studies, animal studies) now needs a second factor: a second database with the same label, or matching wording in the title or abstract (for example the word "case" for a case report, or an animal species for the MeSH term Animals). Exclusions based on wording in the title or abstract are unchanged.
- Automatic exclusion: a label is also overruled when another label points the other way. A Scopus or Web of Science document type "Article", or a PubMed type such as a trial, cohort or observational study, keeps a record that PubMed labels a review, systematic review, editorial or letter. A PubMed trial label (randomised controlled trial, clinical trial) keeps a record from every label-based exclusion.
- Automatic exclusion: the MeSH combination "Animals without Humans" no longer excludes a record whose title describes a human trial or names patients, humans or participants, or whose abstract says patients or participants were treated.
- Found when a randomised controlled clinical trial in humans was excluded because its PubMed record carried the MeSH term Animals and no Humans term, and an original retrospective study was excluded because its PubMed record carried the publication type Letter.
- Effect: fewer records are excluded automatically. Records excluded only by a label from a single database now stay in for screening.

## 1.2.2

- Fix: a title (or other field) containing a hidden line-separator character (U+2028, U+2029 or U+0085) made the reader drop the whole field, so the record had no title and could not be matched to its other copies. Such characters are now replaced by a space when a file is read. Found when a validation showed records with no title. In the reference review in which it was found, 3 duplicates were left in by 1.2.1 because of it.

## 1.2.1

- Research version only: new adjudication choice "Same paper is also in the reference list (the tool could not match the two copies, e.g. no title): not an error" for records listed as only in Winnow. Such records are counted as matched, so a matching failure caused by missing titles is not scored as an error for either method. The accuracy summary CSV has one new last column with this count.
- Automatic exclusion: a study with both an in-vitro and a clinical part is kept for screening. A title containing "clinical", or an abstract mentioning a clinical part or patients/participants being treated, now stops the in-vitro rule.
- Automatic exclusion: random-allocation wording ("randomly assigned", "randomly allocated", "random assignment", "were randomised") now also marks a record as a trial, so a trial that calls itself a case-control or cohort study is not excluded on a MeSH term alone.

## 1.2.0

- Automatic exclusion: the phrases "retrospectively registered" and "retrospective registration" no longer count as evidence of a retrospective study.
- Automatic exclusion: a record that describes itself as a randomised or clinical trial (and is not itself a review) is no longer excluded on a database label (PubMed publication type, Scopus or Web of Science document type), a MeSH term or retrospective wording in the abstract alone. It stays in the screening list.
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
