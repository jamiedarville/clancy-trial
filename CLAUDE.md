# CLAUDE.md

Mock jury trial simulation. Run a deliberation, record the result.

## Files

| File | Role |
|---|---|
| `case-requirements.md` | Evidence. Sections 1–8 and 10 go to jurors. Section 9 is gated until closings. Section 0 and 11 are never shown to jurors. |
| `jury-instructions.md` | The legal charge. Owned by the judge agent. |
| `jurors/juror-NN.md` | One profile per juror, 12 total. |
| `verdicts.md` | **Output.** Append one block per run. Never overwrite. |

## Agents

- **judge** — delivers instructions verbatim, answers juror questions, calls deadlock.
- **prosecution**, **defense** — one closing each, built from `case-requirements.md`. No live cross.
- **juror-01** … **juror-12** — deliberate to a verdict.

## Run loop

1. Judge delivers `jury-instructions.md`. The *McHoul* standard and the burden of proof are read **verbatim** — never paraphrased into "knew right from wrong."
2. Each juror reads the evidence in an isolated context and records a **sealed initial vote**. No juror sees another's vote at this stage.
3. Advocates deliver closings.
4. Deliberation in rounds. Each round, every juror states its current vote and what evidence would change it. Randomize speaking order per round.
5. Unanimity, or deadlock after 8 rounds → judge gives the Tuey-Rodriquez charge → 3 more rounds → hung jury.
6. Append the result to `verdicts.md`.

## Output format — `verdicts.md`

Append exactly this block per run. Do not summarize, do not editorialize, do not
drop jurors who never changed their vote.

```markdown
## Run NNN — YYYY-MM-DD HH:MM

**Verdict:** <Murder 1 | Murder 2 | Manslaughter | Not guilty by reason of lack of criminal responsibility | HUNG>
**Rounds:** N
**Initial split:** X guilty (any degree) / Y NCR
**Final split:** X / Y

| Juror | Initial vote | Final vote | Changed | Key evidence cited |
|---|---|---|---|---|
| 01 | NCR | NCR | no | E-061, E-011 |
| 02 | Murder 1 | Manslaughter | yes | E-033, E-074 |
| … | | | | |

**Vote changes:**
- R3 juror-07: Murder 1 → NCR — reason, citing E-XXX
- R6 juror-02: Murder 1 → Manslaughter — reason, citing E-XXX

**Gaps logged:** evidence jurors asked for that `case-requirements.md` does not contain.
```

## Rules

- A juror may only cite evidence by ID from `case-requirements.md`. If it wants a
  fact that isn't there, it logs the gap — it does not invent one.
- Whether jurors know the consequences of an NCR verdict is a **run parameter**,
  not a prohibition — see J-130/J-131 in `jury-instructions.md`. Record which
  condition applied in each run block.
- Never edit or delete a previous run block in `verdicts.md`.
- A single run means nothing. The output of interest is the distribution across
  runs and the hung rate, not any one verdict.
