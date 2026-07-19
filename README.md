# asd-ste100 skill

A Claude Code skill for writing, rewriting, and checking technical text against ASD-STE100 Simplified Technical English (Issue 9, 2025). It handles the procedural/descriptive split, verb-form restrictions, 20- and 25-word sentence limits, and the controlled-vocabulary approach that keeps maintenance documentation unambiguous.

## Disclaimer

This is an unofficial study and writing aid. It has no affiliation with ASD (Aerospace, Security and Defence Industries Association of Europe) or the Simplified Technical English Maintenance Group (STEMG), and it is not certified by either.

ASD-STE100 is a registered EU trademark (No. 017966390). This skill paraphrases the standard's rules for teaching purposes. It does not reproduce the specification text or the controlled dictionary in full. Download the official document, free, from asd-ste100.org.

No tool can guarantee STE compliance. The human writer signs off on the final text. ASD and STEMG recognize only STEMG members and UNINETTUNO-certified trainers for STE training.

## How the skill thinks about STE

ASD-STE100 is a controlled natural language with two parts: 53 writing rules split into 9 sections, and a controlled dictionary of roughly 900 approved words where each word has one meaning and one part of speech. The rules force short sentences, active voice (with narrow exceptions), and direct commands in procedures. The dictionary blocks synonyms: `start` is approved, `begin` and `commence` are not.

The standard was built in the 1980s because European airlines were translating maintenance manuals into four or five languages for non-native mechanics, and misunderstandings were causing real safety problems. It is still mandatory for ATA iSpec 2200 and S1000D documentation, and it shows up in defense, medical devices, and wind energy.

## What's in the files

- `SKILL.md` — the workflow: classify text type, apply the rules, transform and verify
- `references/writing-rules.md` — the 9 rule sections spelled out
- `references/dictionary.md` — the 4-column dictionary format and how to look words up
- `references/checklist.md` — a compliance pass and the most common mistakes
- `references/background.md` — history, governance, Issue 9 changes, adoption

## Install

Drop the `asd-ste100/` directory into `~/.claude/skills/`. Claude Code or `~/.agents/skills/`. Codex/Opencode picks it up without extra setup.
