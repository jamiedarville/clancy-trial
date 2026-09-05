# juror-axes.md

How the twelve juror profiles were built, and what that does and does not buy you.

## The problem this solves

If profiles are written as personalities, whoever writes them decides the verdict
at authoring time. "Retired police sergeant, no patience for excuses" and
"paediatric nurse whose sister has bipolar disorder" aren't jurors — they're a
theory of the case wearing costumes, and the deliberation just plays it out.

So the profiles are coordinates in an attitudinal space, not characters. Each juror
is a vector on seven axes. The behavioural text for each score is written **once**
per axis level and applied mechanically. Juror 05's text at MIF5 is byte-identical
to any other juror's text at MIF5. Nothing is hand-tuned per juror.

## The seven axes

| Code | Dimension | Grounding |
|---|---|---|
| IDA | Insanity Defence Attitudes | Insanity Defense Attitudes–Revised (Skeem & Golding). The strongest single predictor of verdict in NGRI cases in the empirical literature. |
| LA | Legal Authoritarianism | Revised Legal Attitudes Questionnaire (Kravitz et al.). Predicts conviction-proneness generally. |
| NFC | Need for Cognition | Cacioppo & Petty. Systematic vs. heuristic processing — determines whether a juror engages the element structure or the overall narrative. |
| BJW | Belief in a Just World | Lerner. Relevant here because an unexplained catastrophe creates pressure toward a version in which something accounts for it. |
| MIF | Mental Illness Familiarity | Contact-based stigma measures. Contact predicts willingness to credit psychiatric testimony. |
| EXP | Deference to Expert Testimony | Relevant in any battle-of-experts case, and this trial is nothing else. |
| CONF | Conformity Pressure | Asch-type susceptibility. Determines holdout behaviour and hung-jury rate. |

Axes are named after real constructs because that is where they come from. They
are **not** validated instruments as implemented here, and a score of 4 on MIF is
not a measurement of anything. Treat them as a structured way of varying jurors,
not as psychometrics.

## Assignment

Each axis received the same multiset of levels across the twelve jurors —
`[1,1,2,2,2,3,3,3,4,4,4,5]` — independently permuted. This forces marginal balance
(no axis is skewed across the panel) and drives designed inter-axis correlation
toward zero, so no axis acts as a proxy for another and none is a hidden proxy for
a verdict.

Seeds were searched to minimise the maximum absolute pairwise correlation.
**Seed 45068, max |r| = 0.264** across all 21 axis pairs. At n=12 you cannot get
much below that; residual correlation is sampling noise, not design.

Generators are included (`gen.py`, `opt.py`, `build.py`) so the panel is
reproducible and auditable.

## Assignment matrix

| Juror | IDA | LA | NFC | BJW | MIF | EXP | CONF |
|---|---|---|---|---|---|---|---|
| 01 | 5 | 3 | 4 | 3 | 2 | 4 | 3 |
| 02 | 3 | 3 | 4 | 4 | 4 | 3 | 4 |
| 03 | 2 | 2 | 3 | 1 | 4 | 2 | 3 |
| 04 | 2 | 4 | 3 | 1 | 2 | 1 | 4 |
| 05 | 4 | 4 | 2 | 3 | 5 | 3 | 5 |
| 06 | 1 | 5 | 4 | 2 | 3 | 4 | 1 |
| 07 | 2 | 4 | 2 | 4 | 2 | 4 | 4 |
| 08 | 4 | 3 | 2 | 2 | 3 | 1 | 1 |
| 09 | 4 | 1 | 5 | 3 | 1 | 2 | 2 |
| 10 | 3 | 1 | 1 | 2 | 3 | 5 | 2 |
| 11 | 1 | 2 | 1 | 5 | 1 | 2 | 3 |
| 12 | 3 | 2 | 3 | 4 | 4 | 3 | 2 |

Note the combinations that a human author would not have written: juror 06 is
maximally sympathetic to the insanity doctrine and maximally authoritarian; juror
09 is sceptical of the doctrine, civil-libertarian, and the most systematic
reasoner on the panel. Those internal tensions are the point. Real jurors are not
internally consistent, and a panel of coherent archetypes is exactly the panel that
produces a predetermined verdict.

## No demographics

Deliberately. Age, occupation, race, sex and family status are absent from every
profile. Assigning them would require me to decide which demographic goes with
which attitude, which reintroduces the authoring bias the axes exist to remove, and
would encode stereotypes as simulation parameters. If you want demographics for
realism of voice, sample them **independently** of the axis scores rather than
matching them to attitudes.

## What this does not fix

- **The behavioural text is still mine.** I wrote what MIF5 means. That is a
  smaller and more auditable intervention than writing twelve people, but it is not
  zero, and it is the main remaining place my priors can enter.
- **Balance is not representativeness.** A uniform spread on IDA is not the
  distribution of insanity-defence attitudes in the Plymouth County jury pool. Real
  voir dire in a case like this removes the extremes on IDA — the actual venire was
  individually questioned, which is required in Massachusetts where lack of criminal
  responsibility is at issue. Your panel is more attitudinally extreme at both ends
  than a real empanelled jury. Expect a higher hung rate than reality as a result.
- **Model convergence is untouched by any of this.** Isolated initial votes and the
  stated-reason requirement mitigate it; they do not solve it.
- **Contamination is the largest threat.** These models know the real case. Rule 2
  in every profile forbids reasoning from it, and instructions of that kind are only
  partly effective. Spot-check early transcripts for jurors citing facts with no
  evidence ID — that is what leakage looks like.

## Sanity checks before you trust a batch

1. Do initial sealed votes vary? If all twelve open at the same verdict, the axes
   are not doing any work and something is wrong with how profiles are being loaded.
2. Does any juror cite a fact with no ID? Contamination.
3. Does deliberation end in under three rounds? Convergence, not agreement.
4. Do any intermediate verdicts (murder 2, manslaughter) ever appear? If never,
   J-118 is not reaching the jurors and the run is effectively binary.
5. Run the panel against a deliberately lopsided fact pattern as a control. If it
   still hangs, the panel hangs regardless of evidence and tells you nothing.
