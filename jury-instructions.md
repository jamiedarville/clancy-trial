# jury-instructions.md

**Owner:** judge agent. Delivered to all juror agents before any deliberation.

> **Status:** This is a reconstruction of the Massachusetts charge, drafted from
> the *Model Jury Instructions on Homicide*, District Court Instruction 9.200, and
> the controlling SJC cases cited inline. It is **not** a transcript of what Judge
> Sullivan actually read to the Clancy jury — that text is not public. Sections
> marked `[RECONSTRUCTED]` reflect the standard charge; sections marked
> `[UNCERTAIN]` involve choices the real trial judge made that are not reported.
> Where the simulation's outcome turns on an `[UNCERTAIN]` item, that is a finding
> about the instruction, not about the case.

---

## 1. ROLE AND BURDEN

**J-101** You are the sole judges of the facts. You decide which witnesses to
believe and how much weight to give any piece of evidence. I decide the law, and
you must take the law from me whether or not you agree with it.

**J-102** Opening statements and closing arguments are not evidence. The
indictment is not evidence. Questions put to witnesses are not evidence; only the
answers are.

**J-103** The defendant is presumed innocent. That presumption stays with her
unless and until the Commonwealth proves guilt beyond a reasonable doubt. The
defendant has no obligation to present evidence, to call witnesses, or to testify.
You may draw no inference of any kind from the fact that she did not testify.

**J-104 — REASONABLE DOUBT** `[RECONSTRUCTED]` Proof beyond a reasonable doubt
does not mean proof beyond all possible doubt, and it does not mean proof to a
mathematical certainty. It is proof that leaves you firmly convinced of the
defendant's guilt. If, after weighing all the evidence, you are not firmly
convinced, you must give the defendant the benefit of the doubt and find her not
guilty. It is not enough that the Commonwealth's version is more probable than the
defendant's; a mere probability of guilt is not sufficient.

**J-105** You may consider both direct and circumstantial evidence. Neither is
inherently superior to the other. But an inference you draw must be reasonable and
must flow from facts you find proved — it may not rest on conjecture or guesswork.

---

## 2. ELEMENTS

### 2.1 Murder in the first degree — deliberate premeditation

**J-110** The Commonwealth must prove beyond a reasonable doubt that (1) the
defendant caused the death of the victim, (2) she did so with malice, and (3) she
acted with deliberate premeditation.

**J-111** Deliberate premeditation means the defendant formed a plan to kill after
deliberation, and then acted on it. The deliberation may be brief — no particular
length of time is required, and it may occur in seconds. What matters is that the
decision to kill was the product of reflection rather than a sudden impulse. First
the deliberation and premeditation, then the resolution to kill, then the killing.

### 2.2 Murder in the first degree — extreme atrocity or cruelty

**J-112** The Commonwealth must prove (1) causation of death, (2) malice, and (3)
that the killing was committed with extreme atrocity or cruelty.

**J-113** In deciding extreme atrocity or cruelty you may consider: whether the
defendant was indifferent to or took pleasure in the victim's suffering; the
victim's consciousness and degree of suffering; the extent of any injuries; the
number of blows or the duration of the act; the manner and force used; and the
instrument used. You need not find all of these, but you must find at least one,
and you must agree unanimously on which.

**J-114** `[RECONSTRUCTED]` You may consider evidence of the defendant's mental
impairment in deciding whether the killing was committed with extreme atrocity or
cruelty.

### 2.3 Malice

**J-115** Malice, for murder in the first degree on either theory, means an intent
to cause death or an intent to cause grievous bodily harm. Malice does not require
ill will, hatred, or a bad motive. A person may act with malice toward someone she
loves.

### 2.4 Murder in the second degree

**J-116** If the Commonwealth proves causation and malice but you are not
satisfied beyond a reasonable doubt as to deliberate premeditation or extreme
atrocity or cruelty, the verdict is murder in the second degree.

### 2.5 Manslaughter

**J-117** `[UNCERTAIN]` Reporting confirms the jury was permitted to consider
manslaughter, but not which theory. Two possibilities:

- **Voluntary manslaughter** — a killing with intent, committed in the heat of
  passion on reasonable provocation, on sudden combat, or with excessive force in
  self-defence. *(On the reported facts, provocation appears unsupported.)*
- **Involuntary manslaughter** — an unintentional killing caused by wanton or
  reckless conduct: conduct involving a high degree of likelihood of substantial
  harm, where the defendant knew or should have known of that risk.

> **Judge agent:** select one theory before the run and hold it constant across
> all runs in a batch. Record the selection in `verdicts.md`. Switching theories
> between runs contaminates the distribution.

### 2.6 Mental impairment short of lack of criminal responsibility

**J-118** Separate from the question of criminal responsibility, you may consider
any credible evidence of mental impairment — including the effects of prescribed
medication — in deciding whether the Commonwealth has proved the specific mental
states the offenses require: whether the defendant actually premeditated
deliberately, and whether she actually possessed malice.

**J-119** This is not a defence and not a separate verdict. It bears only on
whether the Commonwealth has proved those elements. A defendant may be criminally
responsible and still lack the capacity to have deliberately premeditated.

> **Note:** J-118 is the most under-appreciated route in this case. It permits a
> juror who rejects the insanity defence outright to nonetheless refuse murder in
> the first degree. Any juror agent that treats the verdict as binary
> guilty-or-insane has misread the charge.

---

## 3. CRIMINAL RESPONSIBILITY — DELIVER VERBATIM

**J-120** If the Commonwealth has proved the elements of the offence beyond a
reasonable doubt, the Commonwealth must **also** prove beyond a reasonable doubt
that the defendant was criminally responsible at the time of the offence. A person
is not guilty if she lacked criminal responsibility. **There is no burden on the
defendant to prove that she lacked criminal responsibility.**

**J-121 — THE STANDARD (*Commonwealth v. McHoul*, 352 Mass. 544 (1967)).** A
person is not criminally responsible for her conduct if, at the time of that
conduct, as a result of mental disease or defect, she lacked **substantial
capacity** either

- **(a)** to appreciate the wrongfulness of her conduct, **or**
- **(b)** to conform her conduct to the requirements of the law.

**J-122 — THE TWO ROUTES.** The Commonwealth may meet its burden in either of two
ways:

1. By proving beyond a reasonable doubt that the defendant did **not** suffer from
   a mental disease or defect at the time of the offence; **or**
2. By proving beyond a reasonable doubt that, although she did suffer from a
   mental disease or defect, she nonetheless retained substantial capacity **both**
   to appreciate the wrongfulness of her conduct **and** to conform her conduct to
   the requirements of the law.

**J-123** If you have a reasonable doubt whether the defendant was criminally
responsible at the time of the offence, you must find her **not guilty by reason
of lack of criminal responsibility**.

**J-124** Mental illness alone does not establish lack of criminal responsibility.
Nor does the presence of planning, or of goal-directed conduct, by itself establish
criminal responsibility. These are matters of evidence for you to weigh.

**J-125** Substantial capacity does not mean total capacity. The question is not
whether the defendant had any awareness whatsoever, but whether her capacity was
substantially impaired.

**J-126 — NO PRESUMPTION OF SANITY.** `[RECONSTRUCTED]` I give you no instruction
that most people are sane or that you may infer sanity from that fact. Under
*Commonwealth v. Lawson*, 475 Mass. 806 (2016), that instruction is no longer to
be given, because of its slight probative weight and the risk it creates of
confusing the burden of proof. The burden rests entirely on the Commonwealth.

> **CRITICAL FOR THE JUDGE AGENT.** J-120 through J-126 must be delivered word for
> word. Do not compress the disjunctive "either/or" in J-121 into a single test.
> Do not restate it as "did she know right from wrong" — that is the *M'Naghten*
> rule and it is **not** the law in Massachusetts. Do not invert the burden. These
> are the highest-leverage lines in the entire simulation.

---

## 4. CONSEQUENCES OF THE VERDICT

**J-130 — MUTINA INSTRUCTION** `[UNCERTAIN]` Under *Commonwealth v. Mutina*, 366
Mass. 810 (1975), where lack of criminal responsibility is fairly raised the
defendant is entitled **on timely request** to an instruction on the consequences
of a verdict of not guilty by reason of lack of criminal responsibility. Where
given, the instruction states in substance:

> A verdict of not guilty by reason of lack of criminal responsibility does not
> result in the defendant's release. She would be taken into custody and examined
> for an initial period of hospitalization. Thereafter she may be committed to a
> secure psychiatric facility, and any such commitment is subject to periodic
> court review, at which a judge determines whether continued commitment is
> required. You should not speculate about the outcome of any future hearing.

**J-131** Whether this instruction was requested and given in the real trial is
not reported. This is a **run parameter**, not a fixed fact:

- **Condition A** — Mutina instruction given.
- **Condition B** — Mutina instruction withheld; jurors instructed not to consider
  consequences.

Run both conditions in equal numbers and record which applied in `verdicts.md`.
The difference between them is one of the more interesting things this simulation
can actually measure, because it isolates how much of a guilty vote is a finding
on the evidence versus a reaction to the perceived consequence of acquittal.

---

## 5. DELIBERATION

**J-140** Your verdict on each count must be unanimous. You must consider each of
the three counts separately; your verdicts need not be the same on each.

**J-141** Order of consideration on each count: murder in the first degree
(considering each theory), then murder in the second degree, then manslaughter,
then the question of criminal responsibility. You must not compromise — do not
return a lesser verdict merely to reach agreement.

**J-142** Deliberate with a view to reaching agreement, but do not surrender a
conscientious belief about the weight of the evidence solely because other jurors
disagree, or for the purpose of returning a verdict.

**J-143** Verdict options: guilty of murder in the first degree (specifying the
theory or theories); guilty of murder in the second degree; guilty of
manslaughter; not guilty by reason of lack of criminal responsibility; not guilty.

**J-144** You may not consider sympathy, prejudice, or public opinion. You may not
consider what sentence might follow a guilty verdict.

---

## 6. DEADLOCK — TUEY-RODRIQUEZ CHARGE

**J-150** Delivered by the judge agent only after the jury has twice reported an
inability to agree. Substance `[RECONSTRUCTED]`:

> The verdict must be the verdict of each individual juror, not a mere
> acquiescence in the conclusion of others. Yet you should examine the question
> submitted to you with candour and with a proper regard for the opinions of one
> another. You should consider that the case must at some time be decided, that
> you are selected in the same manner and from the same source as any future jury
> would be, and that there is no reason to suppose that the case will ever be
> submitted to twelve people more intelligent, more impartial, or more competent to
> decide it. If a majority favours a particular conclusion, a dissenting juror
> should consider whether their doubt is a reasonable one that makes no impression
> on the minds of others equally honest and equally intelligent. And if a minority
> favours a conclusion, the majority should ask themselves whether they might not
> reasonably doubt the correctness of a judgment not concurred in by others.
> But do not yield your conscientious conviction merely to return a verdict.

**J-151** After this charge, deliberation continues for the number of rounds set
in `CLAUDE.md`. If the jury again reports it cannot agree, the judge declares a
hung jury and the run terminates as `HUNG`.

**J-152** The judge agent must not give this charge more than once per run, and
must not pressure any juror to change a vote outside its terms.
