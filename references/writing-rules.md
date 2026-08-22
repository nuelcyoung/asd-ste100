# ASD-STE100 Writing Rules (Part 1)

Part 1 of the standard contains **53 writing rules organized in 9 sections**. The rules differentiate between **procedures** (instructions) and **descriptions** (explanations). This file summarizes each section and the detailed rules needed to write or verify STE text.

## The 9 Rule Sections

1. **Words** — approved words, technical nouns, technical verbs, spelling
2. **Multi-word nouns** — noun clusters, parts of speech
3. **Verbs** — verb forms, auxiliary verbs, -ing form, active voice
4. **Sentences** — short sentences, vertical lists, connecting words, articles
5. **Descriptive writing** — sentences, verbs, descriptive statements, notes
6. **Procedural writing** — content structure, sentences, paragraphs
7. **Safety instructions** — definitions, how to write them
8. **Punctuation and word count** — punctuation rules, word limits
9. **Writing practices** — sentence constructions, recurring errors, style consistency

## Section 1: Words

- Use only approved words from the dictionary, technical nouns, and technical verbs.
- Each approved word has ONE meaning and ONE part of speech (see `dictionary.md`).
- The dictionary approves a word **for a part of speech**, so tag each word as used before ruling on it. `check` is in the dictionary as a noun; "Check the valve" is still a violation. Procedure and traps: `pos-analysis.md`.
- Spelling follows **American English** per Merriam-Webster. Convert British forms: colour → color, centre → center.

## Section 2: Multi-word Nouns

- Maximum **3 words** per multi-word noun.
- If a noun cluster needs more than 3 words, break it with prepositional phrases.
  - Bad: "main landing gear shock absorber assembly"
  - Better: "shock absorber assembly of the main landing gear"

**The 3-word limit is a ceiling, not a target.** Do not dismantle legal 2- and 3-word clusters into `of`-chains — that makes the text longer and heavier than the source without making it clearer.

| Over-corrected | Correct | Words in cluster |
|---|---|---|
| "the times of the database queries" | "the database query times" | 3 — legal |
| "the errors of the application" | "the application errors" | 2 — legal |
| "the failures of the dependencies" | "the dependency failures" | 2 — legal |

Test: count the words in the cluster. Three or fewer and unambiguous → keep it. Four or more, or ambiguous → use the preposition.

## Section 3: Verbs

Approved verb forms ONLY:

| Form | Example |
|---|---|
| Infinitive | to install |
| Imperative | Install... |
| Simple present | installs |
| Simple past | installed |
| Simple future | will install |
| Past participle (as adjective only) | the installed component |

**The participle must come from an approved verb.** "The installed component" is legal because `install` (v) is approved. "The required parts" is not legal, because `require` is not an approved verb — the participle inherits its base verb's ruling, and reading like a plain adjective does not exempt it. Reduce every participle to its infinitive and rule on that first; if it fails, use an approved adjective (`necessary`) or restructure. The same reduction applies to nominalizations: an approved verb does not approve its noun form.

**Modals: `can` and `must` are approved. The others are not.**

| Approved | Meaning | Non-approved | Handling |
|---|---|---|---|
| `can` (v) | to be able to — "you **can** get access to the jacks" | may, might, could | Use `can`, or state the condition explicitly |
| `must` (v) | obligation — "you **must** have the necessary parts" | should, shall, ought to | Use `must`, or the imperative in procedures |
| `will` | simple future | would | Rewrite in simple present, or use `can` |

`can` and `must` carry meaning. Deleting them from a source sentence changes the claim: a hedged statement becomes an absolute one, or a recommendation becomes a fact. That is a Rule 0 violation (`meaning-fidelity.md`), not a simplification.

NOT allowed:

- **Non-approved modals**: may, might, could, should, would, shall
- **Complex auxiliary constructions**: "must be installing" → "install"
- **Progressive tenses** in any form
- **-ing forms as verbs** — they cause ambiguity. Permitted ONLY as:
  - Technical nouns (e.g., "the opening")
  - Modifiers within technical nouns
- Use **active voice**. In procedures, passive is forbidden. In descriptive writing, use the active voice *as much as possible* (Rule 3.5) — the passive is allowed when the agent is unknown, when the agent is unimportant, or when the active voice would force you to name an agent the source never named. **Never invent an agent to escape the passive.** If every sentence in a passage needs a fabricated subject, the passage is procedural in disguise: reclassify it and use the imperative.

## Section 4: Sentences

- **Procedural texts: maximum 20 words per sentence.**
- **Descriptive texts: maximum 25 words per sentence.**
- Meet the limits by **splitting** sentences, never by deleting content. If a sentence will not fit, ask which proposition needs its own sentence — not which words can go.
- Do not omit sentence parts: keep the subject, the verb, and articles (a, an, the).
- **Correct articles, not just present ones.** Uncountable nouns take no `a`/`an` ("high CPU use", not "a high CPU use"). A generic class takes no `the` ("application errors increase", not "the errors of the application increase"). Choose one treatment for mass nouns such as `data` and record it in the terminology table.
- Use **vertical lists** for complex information and sequences.
- Put **conditions first**: "If X, do Y" — not "Do Y if X."

## Section 5: Descriptive Writing

- Explains how things work, what happened, why something occurs.
- Active voice as much as possible; the passive is allowed when the agent is unknown or unimportant. Never invent an agent to avoid it.
- Maximum 25 words per sentence.
- One topic per paragraph; topic sentence at the START of the paragraph.
- Maximum 6 sentences per paragraph.
- May use descriptive statements and notes.
- **Vary sentence length and construction (Rule 6.5).** Descriptive writing must stay readable. Three consecutive sentences on the same frame ("The teams must…", "The teams must…") is a rule violation, not a neutral style choice — and it is the standard signature of a machine rewrite. Mix constructions: a conditional, a vertical list, a short sentence after two longer ones.

## Section 6: Procedural Writing

- Gives direct commands using the **imperative** form: "Install the component."
- One instruction per sentence — never combine instructions.
- Maximum 20 words per sentence.
- Direct language only: no passive voice, no narrative.

## Section 7: Safety Instructions

- Must start with a **clear command or condition**.
- Three levels with defined formatting: **WARNING**, **CAUTION**, **NOTE**.
- Content may be controlled by legal departments — flag when a rewrite touches warning text, since collaboration with lawyers may be required.

## Section 8: Punctuation and Word Count

- Punctuation rules govern colons, dashes, parentheses, and list punctuation.
- Word-count limits are hard rules: 20 (procedures) / 25 (descriptions) per sentence, 6 sentences per paragraph.

## Section 9: Writing Practices

- Watch recurring error patterns (see `checklist.md`).
- Maintain **consistent terminology** throughout a document — the same object gets the same name every time.
- Keep sentence constructions simple. **Simple is not the same as identical**: consistent terminology applies to the *names of things*, not to sentence shape. Repeating one sentence frame across a paragraph breaks Rule 6.5.
- Accuracy outranks vocabulary. A sentence of approved words that states something false is a worse failure than a flagged non-approved word. See `meaning-fidelity.md`.

## Procedures vs Descriptions — Decision Guide

| Signal | Text type |
|---|---|
| Tells the reader to do something | Procedure |
| Steps, numbered actions, commands | Procedure |
| Explains function, cause, behavior, background | Description |
| States what happened or what a system does | Description |

Never mix the two types within a passage. If source text mixes them, separate instructions from explanations before rewriting.
