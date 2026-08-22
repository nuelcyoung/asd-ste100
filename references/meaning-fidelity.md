# Meaning Fidelity — The Gate That Outranks the Dictionary

STE exists to remove ambiguity, not to remove content. A sentence that uses only approved words but states something false, vague, or incomplete is a **worse** failure than a sentence that keeps one non-approved word. The writer is responsible for the content; the dictionary constrains how the content is worded, and never licenses a change to what it says.

This file is the counterweight to `dictionary.md` and `pos-analysis.md`. Those two files push toward substitution. This one sets the limits on substitution.

## The Rule

**Never change a technical fact to satisfy the vocabulary.**

When an approved word does not carry the meaning you need, you have four moves, in this order:

1. **Restructure the sentence** so the idea is carried by approved words in a different shape. Most cases resolve here.
2. **Use an approved verb phrase** instead of a single word (`get access to` for "access", `make sure that` for "check", `find the cause of` for "diagnose").
3. **Declare a technical noun or technical verb** from the project glossary, and record it in the terminology table.
4. **Keep the accurate word and flag it** as an unresolved item in the deliverable, with the reason.

What you must not do is take the nearest approved word and accept the meaning shift. That is the most damaging failure mode of an automated STE rewrite, because the output looks compliant and reads plausibly.

### The failure this rule prevents

| Source (accurate) | Bad "STE" rewrite | What went wrong | Correct handling |
|---|---|---|---|
| "the maximum amount of data that can be **lost** after a failure" | "the maximum quantity of data that can **decrease** after a failure" | `fall` was blocked for "decrease", so `decrease` was taken as the safe word. Data does not "decrease" in a failure — it is lost. The definition is now wrong. | Restructure and keep the fact: "the maximum quantity of data that the system **can lose** after a failure." |
| "This architecture lets the platform **scale**." | "This architecture helps the platform **to increase**." | `scale` was dropped and its object went with it. Increase what? The sentence now says nothing. | "With this architecture, you can add more application instances when the load increases." |
| "A sudden latency increase **can be** more important than high CPU use." | "A fast increase of the response latency **is** more important than a high CPU use." | The modal was deleted, so a hedged claim became an absolute claim. `can` is approved — the deletion was not even necessary. | "A quick increase in the response latency **can be** more important than high CPU use." |
| "Metrics do not show **whether** the application works." | "These data do not show **that** the application operates correctly." | `that` after a negated verb asserts the proposition instead of questioning it. The meaning inverted. | "This data does not show the condition of the application." Avoids both `that` and `whether`. |

## Pass 1 — Proposition Inventory (run before you rewrite)

Before you rewrite a passage, list its propositions: each fact, each relation, each qualifier. After the rewrite, check the list against the output.

For each proposition, confirm:

- [ ] It is **present** in the output — nothing silently dropped
- [ ] It is **unchanged** — no fact altered to fit a word
- [ ] Nothing was **added** that the source did not say — no invented agents, numbers, causes, or obligations
- [ ] Every **hedge** survives (`can`, "usually", "in most cases"), or its removal is deliberate and correct
- [ ] Every **object** of a transitive verb survives — "increase its capacity", not "increase"

A rewrite that fails any line here is not compliant, whatever its word list says.

## Pass 2 — Substitution Safety

Apply this to every word you replace, not only the hard ones.

1. Write the source word's meaning **in context**, in your own words.
2. Write the candidate replacement's single approved meaning.
3. If the two meanings are not the same, the substitution is invalid. Go to the four moves above.
4. Never invent a ruling to justify a substitution. If you have not verified the candidate against the dictionary (see `dictionary-access.md`), say so. Do not present a guess as approved.

**Antonym and near-miss traps.** These pairs are close enough to pass a quick read and wrong enough to matter:

| Do not substitute | For | Because |
|---|---|---|
| `decrease` | lose, delete, corrupt | A decrease is a change in quantity; a loss is a disappearance of data |
| `fall` | decrease, drop in value | `fall` is gravity only |
| `stop` | fail, break down | A stop can be intentional; a failure is not |
| `find` | detect, monitor | Finding is an event; monitoring is continuous |
| `change` | migrate, convert, update | A change is unspecified; the source named a specific operation |
| `make sure that` | verify, validate, test | Use it only when the source means confirmation, not a formal test procedure |
| `many` / `much` | multiple, more than one, several | See the quantifier note below |
| `help` | let, permit, make possible | "Help X to Y" implies partial assistance; "let X Y" implies capability |

**Quantifiers with no fixed number.** `dictionary.md` says to give the exact number or delete the vague quantifier. When the count is variable by design (instances, replicas, microservices), neither move works. Use **"more than one"**, or state the mechanism: "The service operates on more than one instance." Do not reach for "multiple" or "several" as a synonym for "many" — that changes one unverified word for another.

## Pass 3 — Do Not Invent an Agent

Rule 3.5 asks for the active voice in descriptive writing **as much as possible** — not at any cost. Descriptive writing may use the passive when the agent is unknown, when the agent is unimportant, or when the active voice would force you to name someone the source did not name.

To invent a subject and escape the passive is a fabrication:

| Source | Fabricated rewrite | Problem | Better |
|---|---|---|---|
| "Backups should be taken frequently." | "**The teams** must make backups frequently." | The source never said which teams, or that this is their obligation | "Make backups frequently." (procedural) or "Backups are made at frequent intervals." (descriptive, agent unknown) |
| "Recovery procedures must be tested." | "**The teams** must do tests of the recovery procedures." | The same invention, repeated | "Test the recovery procedures." |

If a passage needs an agent on every sentence and the source supplies none, the passage is usually **procedural** in disguise. Reclassify it and use the imperative. That removes the passive and the invented agent at the same time.

**Repetition check:** if the same subject opens more than two consecutive sentences ("The teams must…", "The system does…"), you have either invented an agent or missed a reclassification. Fix the cause, not the surface.

## Pass 4 — Do Not Trade Prose Quality for Compliance

The items below are compliance items, not style preferences. Each has a rule behind it, and each was broken by the "safe" rewrite in the example above.

### Articles and countability (Rule 4 keeps articles — it does not add wrong ones)

"Do not omit articles" does not mean "put an article on everything."

| Wrong | Right | Why |
|---|---|---|
| "a high CPU use" | "high CPU use" | `use` here is uncountable — no indefinite article |
| "much traffic occurs" | "the traffic is high" | Keep the countability natural |
| "These data do not show…" | "This data does not show…" | Choose one treatment of `data` and record it in the terminology table |
| "the errors of the application increase" for a general statement | "application errors increase" | A generic class takes no definite article |

### Noun phrases: 3 words is a ceiling, not a target (Rule 2)

The 3-word limit tells you when a noun cluster is **too long**. It does not tell you to dismantle legal 2- and 3-word noun phrases into `of`-chains. To break short, clear clusters produces heavier text than the source.

| Over-corrected | Correct | Note |
|---|---|---|
| "the times of the database queries" | "the database query times" | 3 words — legal, and shorter |
| "the errors of the application" | "the application errors" | 2 words — legal |
| "the failures of the dependencies" | "the dependency failures" | 2 words — legal |
| "the health of the infrastructure" | "the infrastructure health" | 2 words — legal |
| "main landing gear shock absorber assembly" | "the shock absorber assembly of the main landing gear" | 5 words — this one needs the prepositional phrase |

**Test:** count the words in the cluster. Three or fewer and unambiguous → keep it. Four or more, or ambiguous → use the preposition.

### Chained nominalizations

`of`-chains and stacked abstract nouns defeat the purpose of the standard even when every word is approved.

| Avoid | Use |
|---|---|
| "the engineers go from the detection of a problem to the diagnosis and to the recovery" | "With this information, engineers can find a problem, find its cause, and then correct it." |
| "the speed of the detection" | "how quickly you find the problem" |
| "for the diagnosis of performance problems" | "to find the cause of performance problems" |

### Vary the construction (Rule 6.5, descriptive writing)

Descriptive writing must vary sentence length and construction. A page of identical frames ("The X must do Y", repeated) is a rule violation, not a neutral style choice. It is what makes machine-rewritten STE unreadable.

Check any descriptive passage for:

- [ ] The same sentence opener used more than twice in a row
- [ ] Every sentence at approximately the same length
- [ ] Every paragraph built as subject + `must` + verb

Fix it by mixing constructions: a conditional sentence ("If the primary database stops, the replicas continue to answer read requests."), a vertical list, an imperative where the passage is really procedural, and a short sentence after two longer ones.

## Pass 5 — Do Not Delete Information to Get Under the Word Limit

You meet the 20/25-word limits by **splitting** sentences, never by deleting content.

| Source (28 words) | Wrong — object and condition deleted | Right — split |
|---|---|---|
| "A rollback is a possible step if the last release caused the incident, but it will not help if the cause is a data migration." | "A rollback is a possible step." | "If the last release caused the incident, a rollback is a possible step. If a data migration caused the incident, a rollback does not correct the problem." |

If a sentence will not fit, ask which proposition needs its own sentence. Never ask which words can go.

## Worked Example — A Monitoring Description

**Source:** "Recovery point objective (RPO) defines the maximum amount of data loss that is acceptable, measured as the time between the failure and the last usable backup."

**Bad rewrite — compliant-looking, meaning damaged:**

> "The recovery point objective is the maximum quantity of data that can decrease after a failure."

Failures: `decrease` for "loss" (Pass 2, fact changed); the measurement clause deleted (Pass 5, information lost); "acceptable" dropped, which turns a business threshold into a physical maximum (Pass 1, qualifier lost).

**Correct rewrite:**

> "The recovery point objective is the maximum quantity of data that the system can lose after a failure. This quantity is the time between the failure and the last usable backup."

Two descriptive sentences, 18 and 14 words, active voice, no invented agent, every proposition kept. `lose` (v) goes on the flag list for dictionary verification. If it is not approved, the fallback is a technical-noun declaration of "data loss" from the project glossary — **not** a substitution that changes the fact.

## Reporting Unresolved Words

When accuracy and the dictionary genuinely conflict and no restructure works, say so in the deliverable instead of hiding it:

> `lose` (v) — kept. No approved word carries "data that is gone after a failure"; `decrease` and `fall` change the technical meaning. Verify against Part 2, or declare "data loss" as a technical noun from the project glossary.

An honest flagged word is a compliant deliverable with one open item. A silent bad substitution is an incorrect document.
