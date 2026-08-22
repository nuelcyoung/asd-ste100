# Part-of-Speech Analysis

STE's core rule is "one word, one meaning, **one part of speech**." A word-list check that ignores part of speech (POS) passes text that the standard rejects, because the dictionary approves a word *for a specific POS only*. `check` is in the dictionary, so a naive lookup says "approved" — but it is approved as a noun, and "Check the dependencies" uses it as a verb.

Never rule on a word in isolation. Tag it as used in its sentence, then look it up with that tag.

**A failed ruling tells you to fix the sentence. It does not authorize a swap.** This file finds violations; it does not choose replacements. Every substitution it leads to must first pass substitution safety in `meaning-fidelity.md`: the source word's meaning in context must equal the replacement's approved meaning. When a word fails and no approved word carries the meaning, restructure the sentence, declare a technical term, or keep the word and flag it. Taking the nearest approved word is how a POS-clean rewrite ends up stating something false.

## The Rule

A word passes only if **all three** match the dictionary entry:

1. The word form is listed (or it is a declared technical noun/verb)
2. **The POS as used matches the POS in the entry**
3. The sense as used matches the single approved meaning

Fail any one of the three and the word must be replaced, or declared as a technical noun/verb with a source.

## Step 1: Tag Every Content Word in Context

Work sentence by sentence. For each content word, record the POS it carries *in that sentence*, not the POS it usually has:

| Word in context | POS as used | Why it is easy to get wrong |
|---|---|---|
| "**Check** the valve" | verb (imperative) | Sentence-initial imperatives look like nouns in a word list |
| "Do a **check** of the valve" | noun | Same string, different POS, different ruling |
| "the **required** parts" | adjective (past participle) | Inherits the ruling of the verb `require`, not of a standalone adjective |
| "the **operating** pressure" | modifier in a technical noun | Legal only inside a declared technical noun |
| "**Torque** the bolt" | verb (noun→verb conversion) | Conversions are invisible to a plain word-list check |
| "before the **installation**" | noun (nominalization) | Derived from an approved verb, but the noun form needs its own ruling |

Imperative verbs and noun→verb conversions are the two POS errors a word-list checker misses most often. Tag them explicitly.

## Step 2: Resolve Derived Forms Before Lookup

Derived forms do not inherit approval automatically. Reduce each to its base form, rule on the base, then apply the form rule.

### Past participle used as an adjective

Approved verb forms include the past participle **as an adjective only** — but the participle must come from a verb that is approved in the dictionary, or from a declared technical verb.

- `install` is an approved verb → "the **installed** component" is legal
- `require` is **not** an approved verb → "the **required** parts" is **not** legal, even though it reads as a plain adjective

Procedure: strip the participle to its infinitive → look up the infinitive as a verb → if the verb fails, the participle fails. Replace with an approved adjective (`necessary`) or restructure the sentence.

### -ing forms

Not allowed as verbs. Legal only as a technical noun ("the opening") or as a modifier inside a declared technical noun ("the operating pressure"). Rule on the technical noun as a unit, not on the -ing word alone.

### Nominalizations

A noun derived from an approved verb is not approved by inheritance: `install` (v) being approved says nothing about `installation` (n). Look the noun up on its own. If it fails, convert to a verb phrase with an agent ("before you install the software") or declare it a technical noun.

### Noun→verb conversion

English converts nouns to verbs freely; STE does not. If the dictionary lists a word as a noun, using it as a verb is a violation regardless of how natural it sounds. Rewrite with an approved verb, or use the `do a [noun] of` pattern where the dictionary supports it.

## Step 3: Look Up With the POS Tag

Search the official PDF with the POS marker as printed: `check (n)`, `install (v)`. If the entry's POS differs from your tag, the word fails for that use even though the string appears in the dictionary. Record the ruling as *word + POS*, never as the bare word — a report that says "`check`: approved" is the bug this analysis exists to prevent.

## Confirmed POS Rulings

| Word | Approved as | Not approved as | Use instead |
|---|---|---|---|
| `check` | noun | verb | `examine`, `make sure (that)`, or `do a check of` |
| `require` | — (not approved) | verb, and therefore `required` as a participle adjective | `necessary` (adj), or `you must have` |
| `fall` | verb, "move down by gravity" only | verb meaning "decrease" | `decrease` |
| `about` | preposition, "concerned with" only | adverb meaning "approximately" | give the number, or `approximately` if approved in the project glossary |

## Flag for Lookup — POS Traps

These are **not rulings**. They are shapes that need a POS-tagged lookup before use, because each is commonly written in a POS the dictionary may not approve:

| Shape | Example of the risky use | What to verify |
|---|---|---|
| Noun used as a verb | "**pressure** the system", "**torque** the bolt", "**service** the unit", "**position** the lever", "**sample** the fluid" | Is the word approved as a verb, or as a noun only? |
| Verb used as a noun | "the **run** of the pump", "a **change** of the filter" | Is the noun form listed separately? |
| Past participle as adjective | "the **selected** mode", "the **affected** area", "the **damaged** part" | Is the base verb approved? |
| -ing modifier | "the **operating** pressure", "the **rotating** shaft" | Is the whole phrase a declared technical noun? |
| Nominalization | "the **configuration**", "the **identification**" | Is the noun itself approved, or does it need a verb phrase / technical-noun declaration? |
| Adjective from a non-approved verb | "**accessible**", "**adjustable**" | Rule on the base verb, then on the adjective form |

## Worked Example

**Draft (non-compliant):** "Check all required dependencies before you start the installation."

Sentence type: procedural → 20-word limit, imperative, active voice. Length and voice pass. The failures are all POS-level:

| Word | POS as used | Ruling | Fix |
|---|---|---|---|
| `check` | verb (imperative) | Approved as a **noun** only | `make sure (that)`, or keep the noun: `do a check of` |
| `required` | adjective (past participle of `require`) | `require` is **not approved** as a verb, so the participle fails | `necessary` (adj) |
| `all` | determiner | Approved | keep |
| `dependencies` | noun | Not in the dictionary | Declare `dependency` as a technical noun from the project glossary, or use an approved paraphrase |
| `start` | verb | Approved | keep — or remove, see below |
| `installation` | noun (nominalization) | Verify separately from `install` (v); listed as an abstract nominalization in `dictionary.md` | Convert to the verb: "before you install the software" |

**Compliant rewrite:** "Before you install the software, make sure that you have all the necessary dependencies."

14 words, imperative, active, condition first, `dependency` declared as a technical noun.

**Alternative that keeps `check` as a noun:** "Before you install the software, do a check of all the necessary dependencies."

Both rewrites also drop `start the installation` — the nominalization plus `start` added a word without adding meaning once `install` became the verb.

## Reporting

In review output, report POS failures explicitly so the reader can see why an in-dictionary word was rejected:

> `check` — used as a verb; approved as a noun only (Part 2, `check (n)`). Replace with `make sure (that)` or `do a check of`.
> `required` — past participle adjective of `require`; `require` is not approved as a verb, so the participle is not approved. Replace with `necessary`.

State the POS in every ruling. "Approved" or "not approved" without a POS is not a usable finding.
