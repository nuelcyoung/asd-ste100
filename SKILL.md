---
name: asd-ste100
description: This skill should be used when the user asks to "write in Simplified Technical English", "rewrite this in STE", "check STE compliance", "apply ASD-STE100", "simplify this technical documentation", "make this manual STE-compliant", mentions ASD-STE100, STE, controlled language, or wants technical procedures, maintenance instructions, or descriptions written to the aerospace technical-documentation standard.
version: 0.5.0
---

# ASD-STE100 Simplified Technical English (STE)

Write, rewrite, and verify technical text against **ASD-STE100 Issue 9** (January 2025). STE is a controlled natural language owned by ASD (Aerospace, Security and Defence Industries Association of Europe). It makes technical text unambiguous, easy to understand, and easy to translate. The standard has two parts: 53 writing rules in 9 sections (Part 1) and a controlled dictionary of about 900 approved words (Part 2).

STE is not simplified English for learners. It is a precise standard that requires strong English proficiency to apply. It adds to, but does not replace, a style guide.

## When to Apply This Skill

- Rewrite existing technical text (manuals, procedures, warnings) into STE
- Write new STE-compliant procedures or descriptions
- Review text for STE compliance and report violations
- Explain STE rules, the dictionary, or the standard

## Rule 0: Meaning Outranks Vocabulary

Before any other step: **never change a technical fact, drop a qualifier, delete an object, or invent an agent in order to satisfy the dictionary.** STE removes ambiguity; it does not remove content. A sentence built entirely from approved words that states something false or empty is a worse failure than a sentence that keeps one flagged word.

This is the failure mode that makes an STE rewrite look compliant and read plausibly while being wrong. Three signatures to watch for in your own output:

- **Nearest-word substitution.** "data that can be lost" → "data that can decrease". `decrease` was approved, so it was taken; the definition is now false. Restructure instead: "the quantity of data that the system can lose".
- **Object amputation.** "helps the platform to scale" → "helps the platform to increase". Increase *what*? A transitive verb keeps its object or the sentence says nothing.
- **Hedge deletion.** "can be more important" → "is more important". Deleting a modal turns a qualified claim into an absolute one. (And `can` is approved — see the verb rules below.)

When no approved word carries the meaning, take these moves in order: restructure the sentence; use an approved verb phrase (`get access to`, `make sure that`, `find the cause of`); declare a technical noun or verb from the project glossary; or keep the accurate word and **flag it** in the deliverable with the reason. Never invent a dictionary ruling to justify a substitution.

Full procedure, trap tables, and the five fidelity passes: `references/meaning-fidelity.md`. Load it for every rewrite.

## Step 1: Identify the Text Type

Each rule depends on whether the text is procedural or descriptive. Classify before you write.

| | Procedures (instructions) | Descriptions (explanations) |
|---|---|---|
| Purpose | Tell the user what to do | Explain how things work, or what happened |
| Voice | Active only, imperative form ("Install the pump") | Active as much as possible; passive is allowed when the agent is unknown or unimportant |
| Sentence limit | Maximum 20 words | Maximum 25 words |
| Structure | One instruction per sentence | One topic per paragraph |

Do not mix procedural and descriptive writing in the same passage.

**Never invent an agent to escape the passive.** Rule 3.5 asks for active voice in descriptive writing *as much as possible*, not at any cost. If the source says "backups should be taken frequently", do not write "the teams must make backups frequently" -- the source never named a team or assigned that obligation. Either keep the descriptive passive (agent unknown) or, more often, recognize that the passage is **procedural in disguise** and use the imperative: "Make backups frequently." Reclassifying removes the passive and the fabricated agent at once.

## Step 2: Apply the Core Rules

**One word, one meaning, one part of speech.** Each approved word has one approved meaning and one part of speech. A word is approved for a specific part of speech. A word can be in the dictionary and still be a violation in your sentence. Examples:

- `start` (v) is approved; `begin`, `commence`, `initiate` are not
- `fall` (v) means "move down by gravity" only, never "decrease"
- `check` is approved as a noun only -- write "do a check of the valve", never "check the valve"
- `about` means "concerned with" only, never "approximately"

**Approved verb forms only:** infinitive, imperative, simple present, simple past, simple future, and past participle as an adjective only ("the installed component").

**Past participles follow their base verb's ruling.** A participle used as an adjective is valid only if its base verb is approved, or is a declared technical verb. `install` (v) is approved, so "the installed component" is correct. `require` is not approved, so "the required parts" is not correct -- even though it looks like an ordinary adjective. Reduce the participle to its infinitive and rule on that first. The same rule applies to nominalizations: `install` (v) being approved does not mean `installation` (n) is approved.

**Modal and auxiliary verbs -- `can` and `must` are approved; the rest are not.**

| Allowed | Use for | Not allowed | Replace with |
|---|---|---|---|
| `can` (v) | ability or possibility: "you can get access to the jacks" | may, might, could | `can`, or state the condition: "If X, then Y" |
| `must` (v) | obligation: "you must have the necessary parts" | should, shall, ought to | `must`, or the imperative |
| `will` | simple future | would | rewrite in simple present or `can` |

Deleting `can` or `must` from a source sentence changes what it claims. Do not drop them to look more "simplified" -- that is a Rule 0 violation, not a simplification.

**Do not use:**

- Non-approved modals: may, might, could, should, would, shall
- Progressive or complex verb constructions ("must be installing" becomes "install")
- -ing forms as verbs -- use them only as technical nouns ("the opening") or as modifiers inside technical nouns
- Passive voice in procedures
- Omitted sentence parts -- keep the subject, verb, and articles

**Structure rules:**

- One instruction per sentence; one topic per paragraph; maximum 6 sentences per paragraph
- Multi-word nouns: maximum 3 words. This is a **ceiling, not a target** -- keep legal 2- and 3-word clusters ("database query times", "application errors") and use prepositional phrases only for clusters of 4 or more, or ambiguous ones. Converting every short cluster to an `of`-chain makes the text heavier than the source
- Put conditions before commands: write "If X, do Y", not "Do Y if X"
- Use vertical lists for complex sequences
- Vary sentence length and construction in descriptive writing (Rule 6.5). Three consecutive sentences on the same frame ("The teams must...") is a violation, not neutral style
- Keep articles correct as well as present: uncountable nouns take no `a`/`an` ("high CPU use", not "a high CPU use"), and a generic class takes no `the`
- Safety instructions (WARNING, CAUTION, NOTE) must start with a clear command or condition

**Spelling:** Use American English (Merriam-Webster). Convert British spellings (colour becomes color).

**Technical nouns and verbs:** Company- or domain-specific terms (for example, "hydraulic pump assembly", "to ream") are allowed even if not in the dictionary, when they come from official documentation or glossaries. Keep non-approved words inside them to a minimum.

## Step 3: Verify Words Against the Dictionary -- With Their Part of Speech

Vocabulary control is where STE reviews most often fail. Short, active sentences are not enough. Every content word must be an approved word (with its one approved meaning and part of speech) or a declared technical noun or verb. Do not rely on memory alone for word rulings.

**Rule on words as they are used, never as text strings.** A word passes only if the form is listed, the part of speech as used matches the dictionary entry, and the meaning matches the single approved meaning. Checking a word against a list without tagging its part of speech is the most common way non-compliant text passes review. For example, "Check all required dependencies" is short, active, and imperative, but it still breaks two dictionary rulings. See `references/pos-analysis.md` for the tagging procedure, the derived-form rules, and that sentence worked through in full. Verify against the real dictionary using the first available source, in this order:

1. **User's official PDF (best source).** Ask the user for their copy of the ASD-STE100 specification. It is free from asd-ste100.org, then Downloads, then Issue 9, after a short request form. If the user provides a file path or a URL to their own copy, read Part 2 (the dictionary) directly with PDF tools: search for each questioned word, then apply the format convention -- UPPERCASE means approved, lowercase means non-approved, column 2 gives the approved meaning or UPPERCASE alternatives. See `references/dictionary-access.md` for the full lookup procedure.
2. **Web fetch (limited).** Fetch asd-ste100.org only to confirm the current issue and to give the user the exact request page. The dictionary is behind the request form -- you cannot scrape it. Do not use unofficial mirror copies found on the web (copyright and accuracy risk).
3. **Built-in fallback.** If no official copy is available, work from `references/dictionary.md` (known rulings and high-risk word tables) and state clearly in the deliverable: *"Vocabulary was checked against known rulings and high-risk patterns only, not against the official ASD-STE100 Part 2 dictionary. Full compliance requires verification against the official standard."*

Verification procedure for any rewrite or review:

1. Build the **terminology table** first: list every name used for each thing in the source text (for example, platform, application, system, software package). Choose one name per thing -- an approved word or a declared technical noun -- record it, and use it everywhere.
2. Extract every content word (nouns, verbs, adjectives, adverbs) from the draft as an occurrence, not as a unique string. The same word in two sentences can have two parts of speech and needs two rulings. Exclude declared technical nouns and verbs and approved function words.
3. **Tag each occurrence with its part of speech in context.** Watch for forms that a plain word list misses: sentence-initial imperatives ("Check the valve" -- verb, not noun), nouns used as verbs ("torque the bolt"), past participles as adjectives ("the required parts"), -ing modifiers, and nominalizations.
4. **Reduce derived forms to their base and rule on the base first.** Participle becomes infinitive; nominalization becomes verb; -ing modifier becomes the technical noun that contains it. A derived form fails when its base verb fails.
5. Look each occurrence up against the dictionary source above with its POS marker (`check (n)`, `install (v)`): is it listed? Does the POS match? Does the single meaning match? Record the ruling as *word + POS* -- writing "`check`: approved" is not a valid finding.
6. Scan for the high-risk patterns in `references/dictionary.md` -- vague quantifiers, subjective adjectives, abstract nominalizations, judgment-based instructions. These fail reviews even when sentences are short and active.
7. Replace or justify every occurrence that fails. In review reports, list each failure with its POS, the ruling, and the ruling source (official dictionary or fallback table).

## Step 4: Transform and Verify

Workflow for converting text to STE:

1. **Inventory the propositions** in the source passage: each fact, relation, and qualifier. This is the list you check the output against in step 12 (`references/meaning-fidelity.md`, Pass 1)
2. Classify each passage as procedural or descriptive
3. **Split** sentences that exceed the 20/25-word limits. Split, never delete -- ask which proposition needs its own sentence, not which words can go
4. Convert passive to active where a real agent exists; convert non-approved modals and progressives to approved verb forms. Keep `can` and `must`
5. POS-tag every content word in context, then verify each occurrence against the dictionary with its POS, and enforce the terminology table (Step 3)
6. **Run substitution safety on every replacement**: state the source word's meaning in context and the candidate's approved meaning, and reject the swap if they differ (Pass 2). Watch the antonym traps -- `decrease` is not "lose", `stop` is not "fail", `find` is not "monitor"
7. Remove vague quantifiers and subjective wording; replace judgment calls with "If X, do Y" decision rules (high-risk tables in `references/dictionary.md`). Where the count is variable by design, use "more than one" rather than reaching for another unverified synonym
8. Convert abstract nominalizations to verb phrases with an agent **that the source supplies**, or declare them as technical nouns. Do not invent the agent
9. Split combined instructions into one instruction per sentence
10. Move conditions to the front of sentences
11. Restore omitted subjects, verbs, and articles -- and check the articles you add: no `a`/`an` on uncountable nouns, no `the` on a generic class
12. **Fidelity check.** Walk the step-1 proposition list against the output: everything present, nothing altered, nothing invented, every hedge and every object of a transitive verb intact
13. **Prose check.** Read the output as a document, not as sentences. Look for a repeated sentence frame, `of`-chains rebuilt from legal 2- and 3-word noun clusters, and paragraphs of uniform length (Pass 4)
14. Run the full checklist in `references/checklist.md`, then report remaining violations and every word you flagged as unresolved

Example transformations:

| Non-STE | STE |
|---|---|
| "Before acceptance of unit..." | "Before you accept the unit, do the specified test procedure." |
| "Rotate the cover until the jacks are accessible." | "Turn the cover until you can get access to the jacks." |
| "The unit must be installed carefully." | "Install the unit carefully." |
| "Check all required dependencies before you start the installation." | "Before you install the software, make sure that you have all the necessary dependencies." |

The last row shows the POS problem: the draft is short, active, and imperative, but still fails twice -- `check` is approved as a noun only, and `required` is a participle of `require`, which is not approved. Neither error is visible without POS tagging.

Rewrites that pass the word check and still fail:

| Draft that looks compliant | Why it fails | Correct |
|---|---|---|
| "the maximum quantity of data that can decrease after a failure" | `decrease` was substituted for "lost". Data does not decrease in a failure -- the definition is now false (Rule 0) | "the maximum quantity of data that the system can lose after a failure" |
| "This architecture helps the platform to increase." | The object of the transitive verb was deleted with the non-approved word. Increase what? | "With this architecture, you can add more application instances when the load increases." |
| "A fast increase of the response latency is more important than a high CPU use." | `can be` deleted (a hedge, and `can` is approved); `a` on the uncountable "CPU use" | "A quick increase in the response latency can be more important than high CPU use." |
| "The teams must do tests of the recovery procedures." | Agent invented to avoid the passive; the passage is procedural | "Test the recovery procedures." |
| "the times of the database queries" | A legal 3-word cluster was broken into an `of`-chain | "the database query times" |

When you check (not rewrite) text, report each violation with: the rule broken, the offending text, the part of speech that made it a violation, and a compliant rewrite.

## Copyright and Accuracy Constraints

- This skill is an unofficial aid. It is not affiliated with or endorsed by ASD or STEMG. ASD-STE100 is a registered trademark of ASD.
- The full dictionary (about 900 approved and about 1200 non-approved words) is copyrighted by ASD (EU Trade Mark 017966390). Do not reproduce it in deliverables. Reading the user's own legitimately obtained copy to verify words is normal use of their document. Quote individual rulings. Do not bulk-extract Part 2. For authoritative access, direct users to the free official standard at **asd-ste100.org**.
- No tool (including this skill) can guarantee STE compliance. Final approval always rests with the human writer. Say this when you deliver checked text.
- ASD/STEMG do not endorse any checking tools or non-accredited training.

## Additional Resources

### Reference Files

Load these as needed. Do not load all of them by default:

- **`references/meaning-fidelity.md`** -- Rule 0 in full: the five fidelity passes (proposition inventory, substitution safety, invented agents, prose quality, information loss), the antonym and near-miss trap tables, article and countability rules, noun-cluster over-correction, and a worked example. **Load for every rewrite.**
- **`references/writing-rules.md`** -- The 9 rule sections in detail: verb forms, sentence structure, multi-word nouns, safety instructions, -ing form rules, procedures vs descriptions
- **`references/pos-analysis.md`** -- Part-of-speech tagging procedure, derived-form rules (past participles, -ing forms, nominalizations, noun-to-verb conversion), confirmed POS rulings, POS trap table, worked example
- **`references/dictionary.md`** -- The 4-column dictionary format, lookup technique, known approved and non-approved rulings, high-risk word pattern tables, technical nouns and verbs
- **`references/dictionary-access.md`** -- How to verify words against the official Part 2 dictionary: obtaining the free official PDF, tiered access (local PDF, web fetch, fallback), per-word and bulk lookup procedures
- **`references/checklist.md`** -- Full compliance checklist (fidelity pass first), prose-quality items, the most common writing errors, and the writer and organization best-practice lists
- **`references/background.md`** -- History, governance (STEMG), Issue 9 changes, industry adoption, training and certification, tools landscape, misconceptions, comparison with other controlled languages

For rewriting tasks, load `meaning-fidelity.md`, `writing-rules.md`, `dictionary.md`, `pos-analysis.md`, and `dictionary-access.md`. Load `checklist.md` for compliance reviews. Load `background.md` only for questions about the standard itself. Load `pos-analysis.md` for any word-level ruling, whether rewrite or review. Never run a rewrite on `dictionary.md` and `pos-analysis.md` alone -- those two files push toward substitution, and `meaning-fidelity.md` is what stops a substitution from damaging the content.
