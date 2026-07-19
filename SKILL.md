---
name: asd-ste100
description: This skill should be used when the user asks to "write in Simplified Technical English", "rewrite this in STE", "check STE compliance", "apply ASD-STE100", "simplify this technical documentation", "make this manual STE-compliant", mentions ASD-STE100, STE, controlled language, or wants technical procedures, maintenance instructions, or descriptions written to the aerospace technical-documentation standard.
version: 0.1.0
---

# ASD-STE100 Simplified Technical English (STE)

Write, rewrite, and verify technical text against **ASD-STE100 Issue 9** (January 2025), the international standard for Simplified Technical English. STE is a controlled natural language owned by ASD (Aerospace, Security and Defence Industries Association of Europe). It makes technical text unambiguous, easy to understand, and easy to translate. It consists of 53 writing rules in 9 sections (Part 1) plus a controlled dictionary of ~900 approved words (Part 2).

STE is not "baby English" — it is a precise standard that requires strong English proficiency to apply. It supplements, but does not replace, a style guide.

## When to Apply This Skill

- Rewriting existing technical text (manuals, procedures, warnings) into STE
- Writing new STE-compliant procedures or descriptions
- Reviewing/checking text for STE compliance and reporting violations
- Explaining STE rules, the dictionary, or the standard itself

## Step 1: Identify the Text Type First

Every rule application depends on whether the text is procedural or descriptive. Classify before writing.

| | Procedures (instructions) | Descriptions (explanations) |
|---|---|---|
| Purpose | Tell the user what to do | Explain how things work, what happened |
| Voice | Active only, imperative form ("Install the pump") | Active preferred; passive only when the agent is unknown |
| Sentence limit | **20 words maximum** | **25 words maximum** |
| Structure | One instruction per sentence | One topic per paragraph |

Never mix procedural and descriptive writing in the same passage.

## Step 2: Apply the Core Rules

**One word, one meaning, one part of speech.** Each approved word has exactly one approved meaning and one part of speech. Examples:
- `start` (v) is approved; `begin`, `commence`, `initiate` are not
- `fall` (v) = "move down by gravity" only, never "decrease"
- `check` is approved as a noun only, not as a verb
- `about` = "concerned with" only, never "approximately"

**Approved verb forms only:** infinitive, imperative, simple present, simple past, simple future, and past participle as an adjective only ("the installed component").

**Not allowed:**
- Modal verbs: can, could, may, might, should, would
- Progressive/complex constructions ("must be installing" → "install")
- -ing forms as verbs — permitted only as technical nouns ("the opening") or modifiers inside technical nouns
- Passive voice in procedures
- Omitted sentence parts (keep the subject, verb, and articles)

**Structure rules:**
- One instruction per sentence; one topic per paragraph; maximum 6 sentences per paragraph
- Multi-word nouns: maximum 3 words (longer clusters → use prepositional phrases)
- Conditions before commands: "If X, do Y" — not "Do Y if X"
- Use vertical lists for complex sequences
- Safety instructions (WARNING, CAUTION, NOTE) must start with a clear command or condition

**Spelling:** American English (Merriam-Webster). Convert British spellings (colour → color).

**Technical nouns/verbs:** Company- or domain-specific terms (e.g., "hydraulic pump assembly", "to ream") are allowed even if not in the dictionary, when they come from official documentation or glossaries. Minimize non-approved words inside them.

## Step 3: Transform and Verify

Workflow for converting text to STE:

1. Classify each passage as procedural or descriptive
2. Break sentences that exceed the 20/25-word limits
3. Convert passive to active; convert modals and progressives to approved verb forms
4. Replace non-approved words with approved alternatives (see `references/dictionary.md`)
5. Split combined instructions into one instruction per sentence
6. Move conditions to the front of sentences
7. Restore any omitted subjects, verbs, or articles
8. Keep terminology consistent throughout the document
9. Run the full checklist in `references/checklist.md` and report remaining violations

Example transformations:

| Non-STE | STE |
|---|---|
| "Before acceptance of unit..." | "Before you accept the unit, do the specified test procedure." |
| "Rotate the cover until the jacks are accessible." | "Turn the cover until you can get access to the jacks." |
| "The unit must be installed carefully." | "Install the unit carefully." |

When checking (not rewriting), report each violation with: the rule broken, the offending text, and a compliant rewrite.

## Copyright and Accuracy Constraints

- This skill is an unofficial aid, not affiliated with or endorsed by ASD or STEMG. ASD-STE100 is a registered trademark of ASD.
- The full dictionary (~900 approved + ~1200 non-approved words) is **copyrighted by ASD** (EU Trade Mark 017966390) and cannot be reproduced. Work from the rules and known examples; for authoritative word rulings, direct users to the free official standard at **asd-ste100.org**.
- No tool (including this skill) can guarantee STE compliance — final approval always rests with the human writer. Say so when delivering checked text.
- ASD/STEMG do not endorse any checking tools or non-accredited training.

## Additional Resources

### Reference Files

Load these as needed — do not load all of them by default:

- **`references/writing-rules.md`** — The 9 rule sections in detail: verb forms, sentence structure, multi-word nouns, safety instructions, -ing form rules, procedures vs descriptions
- **`references/dictionary.md`** — The 4-column dictionary format, lookup technique, approved/non-approved word examples, technical nouns and verbs
- **`references/checklist.md`** — Full compliance checklist, the 10 most common writing errors, and the writer/organization best-practice lists
- **`references/background.md`** — History, governance (STEMG), Issue 9 changes, industry adoption, training and certification, tools landscape, misconceptions, comparison with other controlled languages

For rewriting tasks, `writing-rules.md` and `dictionary.md` are usually sufficient. Load `checklist.md` for compliance reviews. Load `background.md` only for questions about the standard itself.
