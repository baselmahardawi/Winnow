# Changelog

## 1.2.7

- Automatic exclusion, narrative reviews: a record is no longer excluded as a narrative review when its title shows a different design. A title that says "review of 1001 cases", "a review of 523 procedures", "audit of N patients" or "analysis of N cases" describes a case series, and a title such as "a literature review and pilot study" or "a review and prospective study" describes a primary study together with a review. Such records are kept for screening. This applies to every route to the narrative-review category (title wording, abstract wording, PubMed publication type, Scopus or Web of Science document type). Found during validation, when a literature review combined with a pilot study, and two retrospective case series typed "Review" in PubMed, were excluded as narrative reviews.
- Automatic exclusion, retrospective studies: a title of the form "review of N cases/patients/procedures/subjects/records" or "audit of N ..." now counts as a retrospective study, unless the title also refers to the literature or to published cases. The word "retrospective" no longer excludes a record when it describes what patients recalled rather than the design, as in "retrospective preference", "retrospective opinion" or "retrospective perception". No change to deduplication.

## 1.2.6

- Automatic exclusion: the in-vitro, animal and retrospective categories no longer exclude a record that is itself a review. A title such as "a scoping review of in vitro evidence" or "a systematic review and meta-analysis of animal studies", or an abstract that says "this systematic review", is treated as a review and not as a study of that design. Such records are left to the systematic-review and narrative-review categories, so a user who excludes in-vitro studies but keeps reviews (for example in an overview of reviews) no longer loses them. Found during validation, when a scoping review of in-vitro evidence was excluded as an in-vitro study.
- Automatic exclusion: the category shown for an excluded record no longer depends on the order in which the category boxes were ticked. Categories are now always checked in the same fixed order (case reports, systematic reviews, narrative reviews, editorials and letters, retrospective, in-vitro, animal). Which records are excluded does not change, only the category shown when a record fits more than one.

## 1.2.5

- Automatic exclusion, retrospective studies: the MeSH term "Retrospective Studies" no longer excludes a record when the title or abstract also says "prospective" or "prospectively", or talks about publications, included studies, the literature or a systematic review. Found when a commentary on a systematic review was excluded as retrospective because its abstract said that studies in the review were collected "one prospectively and two retrospectively".
- Automatic exclusion, animal studies: the MeSH term "Animals" (without "Humans") now excludes a record only when the title or abstract names an animal species or says "animal" or "pre-clinical", and the abstract does not mention patients, participants or volunteers, a clinical study, trial or pilot, a non-randomised or multicentre design. Words that describe materials or the setting, such as "porcine-derived membrane", "bovine", "animal-derived" and "in vivo", no longer count as animal wording. Found when a human pilot clinical study was excluded because its PubMed record carried the MeSH term Animals and its abstract mentioned a porcine-derived membrane and "in vivo" healing.

## 1.2.4

- Export buttons: when automatic exclusion is on, the two export buttons now read "Export records to screen" (RIS and CSV) and the files are named `records-to-screen`, because they contain the records left after automatic exclusion, which is the "To screen" figure and not the "Unique records" figure. With automatic exclusion off, the buttons and file names are unchanged. No change to deduplication or to automatic exclusion.

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
