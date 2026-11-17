# Multilingual and multiscript search cookbook

Search is iterative. Begin with exact names and places, then expand using historically plausible variants. Never treat a search variant as proof that two spellings identify the same person.

## Query construction

For each person/place, build a variant set:
- original spelling from the best-known document;
- phonetic spelling in the likely local language;
- historical orthography;
- transliteration in at least one recognized system;
- married/maiden names and patronymics;
- alternate place names and administrative forms;
- common OCR errors, but label them as exploratory only.

Search each important variant in the original script and in the archive's interface language. Preserve exact query strings and outcomes in the search log.

## Bulgarian

Examples (replace bracketed text):
- `"[Име Фамилия]" site:archives.government.bg`
- `"[селище]" "метрични книги"`
- `"[селище]" "църковни регистри"`
- `"[фамилия]" "Държавен архив"`
- `"[селище]" "бежанци" OR "преселници"`
- `"[име]" "екзархийски регистри"`

Try historical spellings, yat-related orthographic variants where relevant, suffixes and gendered surname forms, but do not normalize away the original form.

## Greek

Examples:
- `"[Ονοματεπώνυμο]" μητρώο αρρένων`
- `"[Επώνυμο]" δημοτολόγιο [τόπος]`
- `"[τόπος]" ληξιαρχικές πράξεις`
- `"[τόπος]" ενοριακά βιβλία βαπτίσεις γάμοι θάνατοι`
- `"[τόπος]" πρόσφυγες Μικράς Ασίας μητρώο`
- `site:greekancestry.net "[surname variant]"`

Try monotonic/polytonic forms where the historical source uses them, alternate transliteration, and Greek spellings of non-Greek names. Do not assume a Greek spelling means Greek ethnicity.

## Turkish and Ottoman

Examples:
- `"[Ad Soyad]" nüfus defteri [yer]`
- `"[yer]" "nüfus defterleri" Osmanlı`
- `"[yer]" "şer'iyye sicilleri"`
- `"[yer]" muhacir iskân kayıtları`
- `site:katalog.devletarsivleri.gov.tr "[yer]"`
- `"[family name]" "Atik Nüfus Kütükleri"`

Try Turkish diacritics and undiacritic variants (ş/s, ğ/g, ı/i, ö/o, ü/u, ç/c), but keep them as distinct search forms. Ottoman script queries require correct historical spelling and specialist reading; do not generate pseudo-Ottoman spellings by letter substitution.

## Russian, Ukrainian and regional languages

Search the languages of the historical administration and migration destination:
- `"[Фамилия]" метрическая книга [населённый пункт]`
- `"[Фамилия]" перепись [уезд/округ]`
- `"[Фамилия]" переселенцы OR беженцы [место]`
- `"[Прізвище]" метрична книга [населений пункт]`
- Romanian: `registre parohiale`, `stare civilă`, `recensământ`, `refugiați`.
- Serbian/Croatian: `matične knjige`, `crkvene knjige`, `popis`.
- Macedonian: `матични книги`, `црковни книги`, `попис`.
- Albanian: `regjistra famullitarë`, `gjendja civile`, `regjistrim`.

These are search vocabulary prompts, not a claim that a particular archive has digitised the records.

## Historical place-name matrix

For every locality, maintain:
- exact spelling in the target record;
- modern official name and language;
- historical names in Bulgarian, Greek, Turkish/Ottoman, Russian, Romanian, Serbian or other relevant languages;
- administrative units at each relevant date;
- parish/metropolis/community;
- coordinates only when the place identity is secure;
- candidate alternatives and evidence for/against each.

Do not select a place based only on similar sound. Distinguish villages with identical names and nearby settlements.

## Search escalation

1. Exact phrase + exact original spelling.
2. Name variants + historical locality.
3. Locality + record type, without a name (catalogue discovery).
4. Archive/fonds/series + administrative unit.
5. Adjacent parish/locality and successor-state archives.
6. Migration destination and refugee/settlement lists.
7. Newspaper, court, land, school, military, guild and cemetery sources as targeted leads.
8. Ask the archive or local historian a narrow question with dates, names, variants and exact locality.

## Search result hygiene

Record the query, language, script, date, source and what was inspected. Distinguish zero search hits from a documented negative search of a complete register. Never use search engine snippets as evidence for a relationship.
