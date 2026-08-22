# asd-ste100 skill

[![Skills Playground](https://skillsplayground.com/badges/installs/asd-ste100.svg)](https://skillsplayground.com/skills/asd-ste100/)

A Claude Code skill for writing, rewriting, and checking technical text against ASD-STE100 Simplified Technical English (Issue 9, 2025). It handles the procedural/descriptive split, verb-form restrictions, 20- and 25-word sentence limits, and the controlled-vocabulary approach that keeps maintenance documentation unambiguous.

## Disclaimer

This is an unofficial study and writing aid. It has no affiliation with ASD (Aerospace, Security and Defence Industries Association of Europe) or the Simplified Technical English Maintenance Group (STEMG), and it is not certified by either.

ASD-STE100 is a registered EU trademark (No. 017966390). This skill paraphrases the standard's rules for teaching purposes. It does not reproduce the specification text or the controlled dictionary in full. Download the official document, free, from asd-ste100.org.

No tool can guarantee STE compliance. The human writer signs off on the final text. ASD and STEMG recognize only STEMG members and UNINETTUNO-certified trainers for STE training.

## How the skill thinks about STE

ASD-STE100 is a controlled natural language with two parts: 53 writing rules split into 9 sections, and a controlled dictionary of roughly 900 approved words where each word has one meaning and one part of speech. The rules force short sentences, active voice (with narrow exceptions), and direct commands in procedures. The dictionary blocks synonyms: `start` is approved, `begin` and `commence` are not.

The dictionary is a constraint on wording, never a licence to change content. The skill's Rule 0 is that meaning outranks vocabulary: when no approved word carries the meaning, restructure the sentence, declare a technical term, or flag the word — never take the nearest approved word and accept the meaning shift. "Data that can be lost" rewritten as "data that can decrease" is built from approved words and says something false, which is the worse failure.

The part-of-speech half of the one-word-one-meaning rule is where checking usually goes wrong. The dictionary approves a word *for one part of speech*, so a word can be in the dictionary and still be a violation. `check` is approved as a noun, which makes "Check the dependencies" wrong and "Do a check of the dependencies" right. Past participles inherit their base verb's ruling, so "the required parts" fails because `require` is not an approved verb. The skill tags every word in context before it rules on it, rather than matching strings against a list.

The standard was built in the 1980s because European airlines were translating maintenance manuals into four or five languages for non-native mechanics, and misunderstandings were causing real safety problems. It is still mandatory for ATA iSpec 2200 and S1000D documentation, and it shows up in defense, medical devices, and wind energy.

## What's in the files

- `SKILL.md` — the workflow: meaning fidelity first, then classify text type, apply the rules, verify words against the dictionary with their part of speech, transform and verify
- `references/meaning-fidelity.md` — Rule 0: accuracy outranks vocabulary. The five fidelity passes, the antonym traps that make a rewrite state something false, invented agents, article and noun-cluster over-correction, and how to flag a word that no approved term can replace
- `references/writing-rules.md` — the 9 rule sections spelled out
- `references/pos-analysis.md` — part-of-speech tagging, derived-form rules (past participles, -ing forms, nominalizations, noun-to-verb conversion), and the POS traps a word-list check misses
- `references/dictionary.md` — the 4-column dictionary format, known rulings, and the high-risk word pattern tables (vague quantifiers, subjective wording, nominalizations)
- `references/dictionary-access.md` — how to verify words against the official Part 2 dictionary: obtaining the free official PDF, tiered access (local PDF / web fetch / fallback), per-word and bulk lookup procedures, terminology table format
- `references/checklist.md` — a compliance pass and the most common mistakes
- `references/background.md` — history, governance, Issue 9 changes, adoption

## Install

Drop the `asd-ste100/` directory into `~/.claude/skills/`. Claude Code or `~/.agents/skills/`. Codex/Opencode picks it up without extra setup.
