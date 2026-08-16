# STE Compliance Checklist and Common Errors

Use this file when reviewing text for STE compliance or doing a final pass on a rewrite. Report each violation with: the rule broken, the offending text, and a compliant rewrite.

## Full Compliance Checklist

### Text type
- [ ] Passage classified as procedural or descriptive
- [ ] Procedural and descriptive content not mixed in one passage

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
- [ ] No vague quantifiers (many, several, some, various, numerous, few, most) — numbers given or word deleted
- [ ] No subjective or unmeasurable wording (appropriate, relevant, regular, normal) — measurable criteria given instead
- [ ] No judgment-based instructions ("use your judgment", "depends on") — "If X, do Y" decision rules given instead
- [ ] Abstract nominalizations converted to verb phrases with an agent, or declared as technical nouns
- [ ] American English spelling throughout
- [ ] Terminology consistent — same object, same name, everywhere

### Verbs
- [ ] Only approved forms: infinitive, imperative, simple present/past/future, past participle as adjective
- [ ] No modals (can, could, may, might, should, would)
- [ ] No progressive tenses or complex auxiliary constructions
- [ ] No -ing forms as verbs (only as technical nouns or modifiers within them)
- [ ] Active voice in procedures; passive in descriptions only when agent is unknown

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

1. Unapproved verb forms — progressive tenses, modals like "can" and "may"
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

## Typical Workflow for Creating STE-Compliant Text

1. **Pre-writing** — understand the task; identify procedural vs descriptive content
2. **First draft** — write in standard technical English
3. **Rule check** — apply all 53 writing rules systematically
4. **POS tagging** — tag every content word with the part of speech it carries in its sentence; reduce participles, nominalizations, and -ing modifiers to their base forms (see `pos-analysis.md`)
5. **Dictionary check** — verify each occurrence against the official Part 2 dictionary **with its POS marker** (see `dictionary-access.md`); fallback to known rulings with a disclaimer if no official copy is available
5. **Restructure** — break long sentences, convert passive to active, simplify
6. **Alternative selection** — replace non-approved words with approved alternatives
7. **Technical terms** — add company glossary terms (technical nouns/verbs)
8. **Review** — self-check or peer review against all rules
9. **Editor check** — editor runs a compatibility check if available
10. **Final approval** — the writer approves and is responsible for the content

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
