# Accessing and Verifying Against the Official Dictionary

The Part 2 dictionary is the only authoritative source for word rulings. It is copyrighted by ASD and distributed as part of the full ASD-STE100 specification — free of charge, but behind a request form. This file describes how to get access and how to verify words.

## Getting Access (in preference order)

### Tier 1 — User's official PDF (best)

1. Ask the user: "Do you have a copy of the ASD-STE100 specification? It is free from asd-ste100.org → Downloads → Issue 9, after a short request form."
2. If they give a file path — or a URL to their own copy — open it with PDF tools (`pdf_info` to find the Part 2 page range from the table of contents, then `pdf_search` / `pdf_read_pages` for lookups).
3. Reading the user's own legitimately obtained copy to check words is normal use of their document. Quote individual rulings in reports; never bulk-extract Part 2 into a deliverable.

### Tier 2 — Web fetch (limited)

- Fetch asd-ste100.org only to confirm the current issue number/date and to give the user the exact download-request page (`STE_downloads.html`).
- The dictionary PDF itself is behind the request form — it cannot be fetched or scraped directly.
- Do NOT use unofficial mirror copies of the spec found on third-party sites. Copyright aside, mirrors are often outdated issues with different rulings.

### Tier 3 — Built-in fallback

- Use the known rulings and high-risk word tables in `references/dictionary.md`.
- Mandatory disclaimer in the deliverable: *"Vocabulary was checked against known rulings and high-risk patterns only, not against the official ASD-STE100 Part 2 dictionary. Full compliance requires verification against the official standard."*

## How to Look Up a Word in the Official PDF

1. Search Part 2 only. Use `pdf_search` with the word plus its part-of-speech marker as printed in the dictionary, e.g. `install (v)`, `check (n)`.
2. Apply the format convention:
   - **UPPERCASE word** = approved, for the meaning in column 2, and only that meaning.
   - **lowercase word** = NOT approved. Column 2 gives the approved UPPERCASE alternative(s).
3. Check the part of speech matches the intended use. `check` is approved as a noun only — "do a check," never "check the valve."
4. Check the meaning matches. `fall` is "move down by gravity" only — never "decrease."
5. Read the STE example in column 3 to confirm usage; column 4 shows the non-STE usage to avoid.
6. If the word is not in the dictionary at all, it can still be usable as a **technical noun** or **technical verb** if it comes from official project documentation or a glossary — declare it in the terminology table and use it consistently.

## Bulk Verification of a Draft

1. Build the **terminology table** before writing: every name used for each thing in the source → one chosen approved name (or declared technical noun) → used everywhere.
2. Extract every content word (nouns, verbs, adjectives, adverbs) from the draft **as an occurrence, not as a unique string** — the same word can carry different parts of speech in different sentences and needs a ruling for each. Exclude declared technical nouns/verbs and approved function words (articles, prepositions, pronouns, approved auxiliaries).
3. **Tag each occurrence with its POS in context, and reduce derived forms to their base** (participle → infinitive, nominalization → verb, -ing modifier → its technical noun). See `pos-analysis.md`.
4. Look up each remaining occurrence **with its POS marker**. Record one of: approved for that POS / non-approved → replacement / technical term (with source). A ruling without a POS is not usable.
5. Apply the replacements, then re-scan the high-risk patterns from `references/dictionary.md` (vague quantifiers, subjective adjectives, nominalizations, judgment-based instructions). Word-by-word approval does not fix vague phrases.
6. Report: words replaced (with the POS that failed), words kept as technical terms (with their source), and any word that could not be verified.

## Terminology Table Format

| Thing in the source | Names found in the source | Chosen STE name | Basis |
|---|---|---|---|
| e.g., the software product | platform, application, system, software package | application | Approved word / project glossary |
| e.g., the routing component | middleware, transport mechanism | message router (TN) | Technical noun, project documentation |

Keep this table in the working notes and apply it mechanically across the whole document. Inconsistent naming is one of the most common review failures.
