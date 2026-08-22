# STE Compliance Checklist and Common Errors

Use this file when reviewing text for STE compliance or doing a final pass on a rewrite. Report each violation with: the rule broken, the offending text, and a compliant rewrite.

## Full Compliance Checklist

### Meaning fidelity — run this pass FIRST (see `meaning-fidelity.md`)

A rewrite can pass every other box on this list and still be an incorrect document. Check fidelity before you check words.

- [ ] Proposition inventory taken from the source, and every proposition present in the output
- [ ] No technical fact changed to fit an approved word (`decrease` for "lose", `stop` for "fail", `find` for "monitor")
- [ ] Every substitution passed substitution safety — the source meaning in context matches the candidate's approved meaning
- [ ] No object of a transitive verb deleted with a non-approved word ("helps the platform to increase" — increase what?)
- [ ] No hedge deleted — `can` and `must` are approved and carry meaning
- [ ] Nothing invented: no agents, numbers, causes, or obligations the source did not state
- [ ] Word limits met by splitting sentences, not by deleting content
- [ ] Negated reporting clauses keep their meaning ("does not show **that** X works" asserts X — restructure)
- [ ] Every word kept for accuracy against a failed lookup is **flagged** in the deliverable with its reason
- [ ] No dictionary ruling asserted that was not actually verified

### Prose quality — compliance items, not style preferences

- [ ] No sentence frame repeated more than twice in a row (Rule 6.5 — vary construction)
- [ ] Sentence lengths vary within each descriptive paragraph
- [ ] No agent invented to escape the passive; a passage that needs one on every sentence is reclassified as procedural
- [ ] Legal 2- and 3-word noun clusters kept, not rebuilt as `of`-chains ("the database query times", not "the times of the database queries")
- [ ] No chained nominalizations ("the detection of a problem to the diagnosis and to the recovery")
- [ ] Articles correct, not merely present — no `a`/`an` on uncountable nouns, no `the` on a generic class
- [ ] One treatment of mass nouns such as `data`, recorded in the terminology table

### Text type
- [ ] Passage classified as procedural or descriptive
- [ ] Procedural and descriptive content not mixed in one passage
- [ ] No invented agents to escape the passive — passive kept (descriptive, agent unknown/unimportant) or passage reclassified as procedural

### Words
- [ ] Every word is approved, a technical noun/verb, or has been replaced with an approved alternative
- [ ] Words verified against the official Part 2 dictionary (user's PDF), OR the fallback disclaimer is included in the deliverable
- [ ] Each word used with its single approved meaning and part of speech

### Part of speech (see `pos-analysis.md`)
- [ ] Every content word tagged with its POS **in context** before lookup — occurrences ruled separately, not unique strings
- [ ] Every lookup done with the POS marker (`check (n)`, `install (v)`); POS mismatch treated as a failure even when the string is in the dictionary
- [ ] Sentence-initial imperatives tagged as verbs, not nouns ("Check the valve" — verb use of a noun-only word)
- [ ] No nouns used as verbs (pressure, torque, service, position, sample)
- [ ] Every past participle adjective traced to its base verb, and the base verb is approved or a declared technical verb ("required" ← `require`: fails)
- [ ] Nominalizations ruled on their own, not inherited from an approved verb (`install` approved ≠ `installation` approved)
- [ ] Every -ing modifier sits inside a declared technical noun
- [ ] Findings reported as *word + POS + ruling*, never as a bare word
- [ ] Terminology table built — one approved name per thing, used everywhere (no platform/application/system drift)
- [ ] No vague quantifiers (many, several, some, various, numerous, few, most) — number given, word deleted, or "more than one" when the count is variable by design
- [ ] No subjective or unmeasurable wording (appropriate, relevant, regular, normal) — measurable criteria given instead
- [ ] No judgment-based instructions ("use your judgment", "depends on") — "If X, do Y" decision rules given instead
- [ ] Abstract nominalizations converted to verb phrases with an agent, or declared as technical nouns
- [ ] No vague predicates ("have value", "cause a change", "give help") — subject–verb–object statements naming actor, condition, and action instead
- [ ] No bare subjective comparisons ("more important than", "critical", "essential") — measurable criteria or priority levels instead; hedges kept ("can be more important than")
- [ ] Recognized collocations intact, including their prepositions ("sudden increase", "data loss", "an increase in response latency") — no synonym or preposition swaps inside fixed pairings
- [ ] One grammatical treatment per mass term, document-wide ("this data does" OR "these data do"); no indefinite article on uncountables ("high CPU use")
- [ ] Meaning preservation confirmed against the source (`meaning-fidelity.md`): every proposition present and unchanged, nothing invented, hedges survive, transitive verbs keep their objects
- [ ] Nothing deleted to meet word limits — sentences split, never truncated
- [ ] Naturalness pass done — no chained nominalizations ("go from the detection of a problem to the diagnosis"), no repeated sentence frames
- [ ] American English spelling throughout
- [ ] Terminology consistent — same object, same name, everywhere

### Verbs
- [ ] Only approved forms: infinitive, imperative, simple present/past/future, past participle as adjective
- [ ] No non-approved modals (may, might, could, should, would, shall) — `can` and `must` are approved, and must not be deleted from a source sentence
- [ ] No progressive tenses or complex auxiliary constructions
- [ ] No -ing forms as verbs (only as technical nouns or modifiers within them)
- [ ] Active voice in procedures; in descriptions, active as much as possible — passive kept where the agent is unknown or unimportant

### Sentences
- [ ] Procedures: every sentence ≤ 20 words
- [ ] Descriptions: every sentence ≤ 25 words
- [ ] One instruction per sentence
- [ ] Conditions come first: "If X, do Y"
- [ ] No omitted subjects, verbs, or articles
- [ ] Vertical lists used for complex sequences

### Paragraphs
- [ ] One topic per paragraph
- [ ] Topic sentence at the start
- [ ] Maximum 6 sentences per paragraph

### Multi-word nouns
- [ ] No noun cluster longer than 3 words (longer → prepositional phrases)

### Safety instructions
- [ ] WARNING / CAUTION / NOTE formatted per the standard
- [ ] Each starts with a clear command or condition
- [ ] Legal-controlled warning text flagged rather than silently rewritten

## The 11 Most Common Writing Errors

1. Unapproved verb forms — progressive tenses, and the non-approved modals `may`, `might`, `could`, `should`, `would`. (`can` and `must` are approved — do not delete them)
2. Sentences over the 20/25-word limits
3. Non-approved words used when approved alternatives exist — including vague quantifiers (many, several, some) and subjective wording (relevant, regular, correct)
4. **Approved words used in the wrong part of speech** — `check` (noun only) written as a verb, nouns converted to verbs, and past participle adjectives built from non-approved verbs ("the required parts"). These survive a word-list check and fail a real review
5. Passive voice in procedures
6. Multi-word nouns longer than 3 words without prepositions
7. Omitted subjects, verbs, or articles
8. Topic sentences not at the start of paragraphs
9. Mixed procedural and descriptive text types
10. -ing forms used as verbs instead of as technical nouns
11. Inconsistent terminology across the document

### The 3 errors that survive a clean checklist

These pass a word-and-rule check and fail a human reader. They are the signature of a mechanical rewrite:

12. **Meaning damaged by a safe substitution** — the nearest approved word replaced the accurate one and changed the fact ("data that can decrease" for "data that can be lost")
13. **An invented agent on every sentence** — "The teams must…" repeated down the page, where the source named no team and the passage was really procedural
14. **Over-correction** — legal 2- and 3-word noun clusters broken into `of`-chains, articles added to uncountable nouns, hedges deleted, and objects dropped along with the non-approved verbs that carried them

## Typical Workflow for Creating STE-Compliant Text

0. **Proposition inventory** — list the facts, relations, and qualifiers in the source. This is what you check the finished text against (`meaning-fidelity.md`, Pass 1)
1. **Pre-writing** — understand the task; identify procedural vs descriptive content
2. **First draft** — write in standard technical English
3. **Rule check** — apply all 53 writing rules systematically
4. **POS tagging** — tag every content word with the part of speech it carries in its sentence; reduce participles, nominalizations, and -ing modifiers to their base forms (see `pos-analysis.md`)
5. **Dictionary check** — verify each occurrence against the official Part 2 dictionary **with its POS marker** (see `dictionary-access.md`); fallback to known rulings with a disclaimer if no official copy is available
6. **Restructure** — split long sentences (never delete to fit), convert passive to active where a real agent exists, simplify
7. **Alternative selection** — replace non-approved words with approved alternatives, running substitution safety on each swap; where no approved word carries the meaning, restructure, declare a technical term, or flag the word
8. **Technical terms** — add company glossary terms (technical nouns/verbs)
9. **Fidelity and prose pass** — check the output against the step-0 proposition list, then read it as a document for repeated frames, `of`-chains, and article errors
10. **Review** — self-check or peer review against all rules
11. **Editor check** — editor runs a compatibility check if available
12. **Final approval** — the writer approves and is responsible for the content

## Best Practices for Individual Writers

1. Get trained — take an accredited basic course first
2. Master the rules, not just the dictionary — the 53 rules are the foundation
3. Know the text type — procedural vs descriptive rules differ
4. Use approved alternatives from the dictionary
5. Keep sentences short — 20/25-word limits
6. One thought per sentence and per paragraph
7. Use active voice; passive only in descriptions with an unknown agent
8. Put conditions first
9. Use vertical lists for complex information
10. Review work systematically against each rule

## Best Practices for Organizations

1. Build a terminology database of technical nouns/verbs
2. Validate terms before entry — assign one person for quality
3. Decide the tool strategy — writers or editors run checkers?
4. Establish document workflows with an STE compliance check in the review cycle
5. Separate content from formatting (tools must handle XML markup if needed)
6. Monitor tool accuracy — track false positives/negatives
7. Make training mandatory for all technical writers
8. Stay current — new issues roughly every 3 years
9. Use accredited trainers only (STEMG or UNINETTUNO-certified)
10. Keep a style guide — STE supplements, never replaces it
