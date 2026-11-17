# Research ledger: people, events, sources and proof

This is the operational data model. Keep the research ledger outside the narrative report. Never silently overwrite an earlier conclusion.

## Core entities

Use stable internal IDs, not names, as identifiers.

- `P-000001`: person. One record per *candidate identity* until identity resolution is justified.
- `E-000001`: event (birth/baptism, marriage, death/burial, migration, residence, military service, property, court, occupation).
- `S-000001`: source item (one archival record, register page, image, certificate, published index entry).
- `A-000001`: assertion extracted from a source (e.g. “X is stated to be Y's father”).
- `R-000001`: proposed relationship between two person IDs, with evidence and status.
- `Q-000001`: search action, including unsuccessful searches.
- `L-000001`: place identity / historical jurisdiction record.

A source is not an assertion; an assertion is not automatically a fact; a proposed relationship is not automatically an accepted edge in the tree.

## Minimum person record

```yaml
person_id: P-000001
display_name: ""
name_forms:
  - as_written: ""
    language: ""
    script: ""
    normalized: ""
    transliteration: ""
    system: ""
    source_id: S-000001
    locator: ""
    confidence: "high|medium|low"
sex: "female|male|unknown|as_recorded"
life_dates:
  birth: {from: null, to: null, precision: "unknown"}
  death: {from: null, to: null, precision: "unknown"}
places: []
occupations: []
religious_or_community_affiliation:
  value: null
  source_id: null
  note: "Record only when explicitly evidenced; do not infer ethnicity."
identity_status: "candidate|probable|resolved|disputed"
privacy: "living|deceased|unknown"
notes: ""
```

Do not fill a field because software expects a value. Use null/unknown. Approximate dates must state their derivation (e.g. age at census, not a precise birth date).

## Minimum source record

```yaml
source_id: S-000001
repository_or_publisher: ""
collection_or_fonds: ""
series: ""
document_title: ""
record_date: ""
place_as_written: ""
archive_reference: ""
volume: ""
folio_or_page: ""
image_or_frame: ""
url: ""
access_date: "YYYY-MM-DD"
source_type: "original|contemporary_copy|later_copy|index|transcription|publication|family_testimony|database"
language: ""
script: ""
creator_or_authority: ""
purpose_of_record: ""
coverage_and_gaps: ""
image_saved: false
independence_group: ""
legibility: "clear|partial|poor|not_seen"
```

An online catalogue entry, an image of the original, an index, and a later transcript are separate source items. If they derive from the same underlying register, give them the same `independence_group`.

## Assertion record

Every material statement should be traceable to one or more assertions.

```yaml
assertion_id: A-000001
subject_person_id: P-000001
predicate: "father_of|mother_of|spouse_of|born_on|born_in|resided_in|died_on|occupation|name_as_written|other"
object_person_id: null
value: ""
source_id: S-000001
exact_quote_or_transcription: ""
translation: ""
locator: ""
informant_or_recorded_by: ""
directness: "explicit|implicit|inferred"
reliability_notes: ""
```

Keep transcription, translation, normalization and interpretation in separate fields. Mark illegible characters; do not silently repair them.

## Relationship proof record

```yaml
relationship_id: R-000001
person_1: P-000001
relationship: "parent_child|spouse|sibling|other"
person_2: P-000002
status: "hypothesis|single-source|corroborated|strongly-corroborated|contradicted|unresolved"
supporting_assertions: []
contradicting_assertions: []
independence_assessment: ""
proof_summary: ""
alternatives_considered: []
last_reviewed: "YYYY-MM-DD"
```

A parent-child link should normally be explicit in a reliable record, or established by a documented chain of indirect evidence. Two websites repeating the same index are not independent. A single high-quality original record can be strong evidence but remains single-source until corroborated independently. Do not impose a universal numerical score that conceals source quality.

## Search log, including negative searches

Record:
- exact query, language, alphabet/script and spelling variants;
- repository, collection, filters, date searched and access route;
- what catalogue/register/pages were actually inspected;
- coverage, missing years, unindexed portions and access barriers;
- exact result, including “no result”;
- next action and why.

A failed search is meaningful only if the collection's coverage and search method are known. “No result” is not proof that a person did not exist or live there.

## Evidence analysis checklist

For each proposed identity or relationship:
1. What exactly does each source state, and what is merely inferred?
2. Was the record created close to the event? Who supplied the information?
3. Is the record original, a later copy, an index, or a derivative?
4. Could two records copy the same earlier source?
5. Are names, dates and ages consistent within plausible historical error?
6. Do spouse, parents, children, occupation, address, neighbours, witnesses and chronology fit?
7. Are there same-name candidates or contradictory records?
8. Have alternative explanations been tested (namesake, remarriage, adoption, step-parent, calendar conversion, boundary change)?
9. What additional record could distinguish the candidates?

Use the Genealogical Proof Standard as a working discipline: reasonably exhaustive research for the question, complete and accurate citations, analysis/correlation, resolution of conflicts, and a written conclusion. Do not claim a conclusion meets the standard unless the work actually does.

## FAN / cluster research

When a record is ambiguous, investigate the documented network: family, associates, neighbours, witnesses, godparents, household members, business partners and migration companions. This is a way to generate and test leads, not to assign relationships by proximity. Record each person's own evidence and relationship status.

## DNA evidence (if later supplied)

Treat DNA matches as evidence of shared genetic segments/IBD only within the limitations of the test, platform, population history and statistical model. A match does not by itself identify a common ancestor, exact relationship, ethnicity, or a particular branch. Endogamy, pedigree collapse, small reference populations and multiple shared ancestral paths can inflate apparent closeness. Do not upload raw DNA or identify living matches without explicit user consent. Integrate DNA only as a separate evidence stream and explain uncertainty.

## GEDCOM/export rule

Export only resolved or explicitly user-approved provisional relationships, preserving source citations and notes. Keep hypotheses outside the accepted tree or mark them clearly as hypotheses. Never invent placeholder parents to make a tree look complete.
