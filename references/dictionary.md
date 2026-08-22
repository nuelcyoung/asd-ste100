# ASD-STE100 Dictionary (Part 2)

Part 2 of the standard is a controlled dictionary of approximately **900 approved words** and approximately **1200 non-approved words** with suggested approved alternatives. Words were selected for simplicity, frequency, and ease of recognition.

**Copyright constraint:** The dictionary is copyrighted by ASD (EU Trade Mark 017966390). Do not attempt to reproduce it in full. Apply the known examples and principles below; for authoritative rulings on specific words, verify against the official standard as described in `references/dictionary-access.md` (user's official PDF, or the free copy from asd-ste100.org).

## The 4-Column Format

| Column | Content | Format convention |
|---|---|---|
| **Word (part of speech)** | The word with its approved part of speech | UPPERCASE = approved; lowercase = non-approved |
| **Approved meaning / ALTERNATIVES** | The single approved meaning, or suggested approved replacements | UPPERCASE for approved meanings/alternatives |
| **STE EXAMPLE** | Correct usage | Always uses approved words |
| **Non-STE example** | How the word is misused in standard technical writing | Lowercase; shows what to avoid |

Lookup technique: find the word; if lowercase (non-approved), take the UPPERCASE alternative from column 2; verify the part of speech matches the intended use; confirm the meaning matches the single approved meaning.

Column 1 carries the part of speech for a reason: **the entry approves the word for that POS only.** Search with the marker (`check (n)`, `install (v)`), and treat a POS mismatch as a failure even when the string is present in the dictionary.

## The Core Principle

**One word, one meaning, one part of speech.** Each approved word has exactly one approved meaning and one approved part of speech. All three must match the use in the sentence. See `pos-analysis.md` for the tagging procedure and the rules for derived forms.

## Known Approved-Word Rulings

- `start` (v) — approved. `begin`, `commence`, `initiate`, `originate` are NOT approved.
- `fall` (v) — "to move down by force of gravity" ONLY. Not "to decrease."
- `check` (n) — approved as a noun only. NOT approved as a verb (use "do a check of" or an approved verb such as "make sure" or "examine").
- `require` — NOT approved. Use `necessary` (adj) or "you must have". This also blocks `required` as a participle adjective: "all required dependencies" fails, "all the necessary dependencies" passes.
- `about` (prep) — "concerned with" ONLY. Not "approximately."
- `close` (v) — exactly two meanings: (1) to move together to stop passage ("close the door"), (2) to operate a circuit breaker ("close the circuit"). NOT approved for "close a meeting" or "close a business."
- `can` (v) — **approved**, "to be able to". This is the word the standard's own examples use: "TURN THE COVER UNTIL YOU **CAN** GET ACCESS TO THE JACKS." `may`, `might`, and `could` are NOT approved.
- `must` (v) — **approved**, for obligation. `should`, `shall`, and `ought to` are NOT approved.

Do not treat `can` and `must` as banned modals. They carry meaning, and deleting them changes what the sentence claims — a hedge becomes an absolute, a recommendation becomes a fact.

## When No Approved Word Carries the Meaning

A lookup that fails is not permission to take the nearest approved word. The moves, in order:

1. Restructure the sentence so approved words carry the idea in a different shape.
2. Use an approved verb phrase (`get access to`, `make sure that`, `find the cause of`).
3. Declare a technical noun or verb from the project glossary and record it in the terminology table.
4. Keep the accurate word and **flag it** in the deliverable with the reason.

The substitution tables below tell you what a word means, not that a swap is safe. Run substitution safety on every replacement before you accept it: `meaning-fidelity.md`, Pass 2. `decrease` is not "lose". `stop` is not "fail". `find` is not "monitor".

## Derived Forms Do Not Inherit Approval

A participle, nominalization, or -ing modifier is ruled through its base form:

| Derived form | Rule | Example |
|---|---|---|
| Past participle as adjective | Legal only if the base **verb** is approved or is a declared technical verb | `install` (v) approved → "the installed component" passes; `require` not approved → "the required parts" fails |
| Nominalization | Needs its own entry; approval of the verb says nothing about the noun | `install` (v) approved ≠ `installation` (n) approved |
| -ing modifier | Legal only inside a declared technical noun | "the operating pressure" — rule on the technical noun as a unit |
| Noun used as a verb | Not legal if the entry gives the noun POS only | "torque the bolt" → use an approved verb, or "do a check of" style patterns |

## Transformation Examples

| Non-STE | STE |
|---|---|
| Before acceptance of unit... | BEFORE YOU ACCEPT THE UNIT, DO THE SPECIFIED TEST PROCEDURE. |
| Rotate the cover until the jacks are accessible. | TURN THE COVER UNTIL YOU CAN GET ACCESS TO THE JACKS. |
| Check all required dependencies before you start the installation. | BEFORE YOU INSTALL THE SOFTWARE, MAKE SURE THAT YOU HAVE ALL THE NECESSARY DEPENDENCIES. |

Patterns these illustrate:

- Nominalizations ("acceptance", "installation") become verbs ("you accept", "you install")
- Non-approved verbs ("rotate") become approved ones ("turn")
- Adjectives like "accessible" become verb phrases with approved words ("can get access to")
- Implied subjects are restored ("you")
- Words used in the wrong part of speech are replaced, not kept because the string is in the dictionary ("check" as a verb → "make sure that"; "required" ← non-approved verb `require` → "necessary")

## High-Risk Word Patterns (Skill Guidance)

These patterns cause most real-world review failures — even in text with short, active sentences. This section is derived skill guidance, NOT a reproduction of the official dictionary. Verify rulings against the official source when available (see `references/dictionary-access.md`).

### Vague quantifiers — give the number, delete, or use "more than one"

| Avoid | STE handling |
|---|---|
| many, much, several, some, various, numerous, few, most | Give the exact number ("six services") or delete the word if the number does not matter. When the count is variable by design (instances, replicas, microservices), neither move works — use "more than one" or state the mechanism. Do not swap "many" for another unverified word such as "multiple" |

When the count is **variable by design** — application instances, replicas, microservices, users — neither move works, because there is no exact number and the plurality is the point. Use **"more than one"**: "The service operates on more than one instance." Do not swap `many` for "multiple" or "several"; that trades one unverified word for another and fixes nothing.

### Subjective / unmeasurable wording — give criteria

| Avoid | STE handling |
|---|---|
| appropriate, relevant, regular, normal, correct (as in "the correct action") | Replace with a measurable condition: "at intervals of 100 h", "if the value is more than 5 bar" |
| important, critical, essential, significant, urgent; bare comparatives ("is more important than") | Give the criterion or the priority level: "Give a sudden increase in response latency alert level 1. Give sustained high CPU use alert level 3." If the comparison stays, its hedge stays too ("can be more important than") |
| judgment, "depends on" (as an instruction) | Never tell the reader to judge. Give the decision rule: "If X, do Y. If Y, do Z." |
| "when conditions permit", "if possible" | State the condition measurably: "when a processing node is available" |

### Vague predicates — name actor, condition, action

| Avoid | STE handling |
|---|---|
| "have value", "be of importance", "cause a change", "give help", "have an effect" | Replace with subject–verb–object statements that say who does what under which condition: "Act on an alert only when it shows a condition that you need to correct." Verify every replacement word against the dictionary |

### Collocation traps — do not break recognized pairings

| Avoid | STE handling |
|---|---|
| Synonym swaps inside fixed technical pairings: "fast increase" for "sudden increase"; "data decrease" for "data loss" | Keep the standard pairing and verify its words against the dictionary, or declare the pairing a technical noun. A pairing broken by individually-approved words still fails review |
| Wrong prepositions inside pairings: "an increase of latency" | Use the pairing's preposition: "an increase IN response latency"; spatial containment: "instances IN different availability zones", not "on availability zones" |

### Abstract nominalizations — use verbs or technical nouns

| Avoid (as vague abstractions) | STE handling |
|---|---|
| optimization, implementation, identification, configuration, installation, guidance, capability | Turn into a verb phrase with an agent ("you install", "the system configures"), or declare the term a project technical noun and use it consistently |

### Multi-meaning verbs — pin one meaning

| Risk words | STE handling |
|---|---|
| run, apply, review, change, check, fall, close, about | Use only with the dictionary's single approved meaning and part of speech. If the needed meaning differs, pick a different approved word (e.g., "do a check of" for `check` (n)) |

### Part-of-speech traps — tag before you rule

| Shape | Risky use | Check |
|---|---|---|
| Noun used as a verb | "pressure the system", "torque the bolt", "service the unit" | Approved as a verb, or as a noun only? |
| Past participle as adjective | "the required parts", "the selected mode" | Is the base verb approved? |
| Nominalization | "the configuration", "the installation" | Is the noun listed in its own right? |
| -ing modifier | "the operating pressure" | Is the whole phrase a declared technical noun? |

Full procedure and worked example: `pos-analysis.md`.

## Technical Nouns and Technical Verbs

STE permits company-specific or subject-field-specific terms that are NOT in the dictionary:

- Defined by their subject-field categories.
- Acceptable sources: official documentation, engineering drawings, company glossaries, terminology databases.
- If a non-approved word appears within a technical noun/verb, it becomes part of that term automatically.
- Recommended: minimize non-approved words even within technical terms.

Examples: propeller, hydraulic pump assembly, discoloration, aural warning system (technical nouns); to drill, to ream (technical verbs).

Organizational practice: maintain a validated terminology database with a single person assigned for quality control of new entries.

## Spelling

American English per Merriam-Webster's Dictionary. Convert all British spellings: colour → color, centre → center, organise → organize.
