# Mock Jury Trial Simulation

## What Is This?

This is a computer simulation of a real jury trial. Instead of real people, AI agents play the roles of jurors, lawyers, and a judge. The goal is to see how different jurors with different personalities and beliefs vote on a complex criminal case.

**The Case:** A woman accused of killing her three children. The defense argues she wasn't mentally responsible for her actions; the prosecution argues she was. It's a case about mental illness, the law, and what "not guilty by reason of insanity" means in practice.

## How It Works (Simple Version)

1. **The Judge** reads the laws and instructions to the jurors
2. **Each Juror** reads the evidence alone and votes in private (nobody sees their vote yet)
3. **The Lawyers** present closing arguments — defense first, prosecution last
4. **The Jury** discusses the case in rounds, with jurors explaining their votes and what would change their minds
5. **The Judge** keeps score until all jurors agree, or declares a hung jury if they can't agree after many rounds
6. **The Result** gets recorded in a file

## Who Are the Jurors?

Each juror is an AI with a specific personality profile. There are 7 different personality traits:

- **Insanity Defense Attitudes:** Do you think the insanity defense is legitimate or a loophole?
- **Legal Authoritarianism:** Do you worry more about convicting innocent people or letting guilty people go free?
- **Need for Cognition:** Do you want all the details or prefer the big picture?
- **Belief in a Just World:** Do you need everything to have a clear reason and cause?
- **Mental Illness Familiarity:** Do you understand mental illness from personal experience or just in theory?
- **Deference to Expert Testimony:** Do you trust expert witnesses or are you skeptical of paid experts?
- **Conformity Pressure:** Do you stick to your position or do you feel pressure to go along with the group?

Each juror gets a random score (1-5) on each trait. This creates 12 very different personalities, so they don't all vote the same way.

## The Files Explained

| File | Purpose |
|------|---------|
| **case-requirements.md** | The evidence and facts of the case |
| **jury-instructions.md** | The legal rules the judge reads |
| **verdicts.md** | Where the results are saved (one entry per trial run) |
| **newpanel.py** | The Python script that creates new jurors |
| **juror-axes.md** | Technical details about how jurors are created |

## How to Run a New Trial

### Quick Start

```bash
# Generate a new panel of 12 jurors (Panel 03)
python3 newpanel.py --panel 3

# This creates a folder: .claude/agents/jurors/panel-03/
# Each juror gets their own file with their personality profile
```

### What That Command Does

1. Creates 12 new AI jurors with random personality scores
2. Makes sure they're balanced (no two jurors are too similar)
3. Saves their profiles in a folder
4. Prints information about the panel to your screen

### Run the Trial

Once you have jurors created, Claude Code runs the trial using AI agents:
- The judge delivers instructions
- Jurors vote privately
- Lawyers argue the case
- Jurors deliberate and vote again
- Results are recorded

### More Options

```bash
# Generate panel 2 with a custom output folder
python3 newpanel.py --panel 2 --out /path/to/folder

# Use a specific random seed (for reproducible results)
python3 newpanel.py --panel 4 --start 400000
```

## Understanding the Results

When a trial finishes, look at `verdicts.md`:

- **Verdict:** What did they decide? (Not guilty by reason of insanity, guilty of murder, etc.)
- **Rounds:** How many discussion rounds did it take?
- **Initial split:** How did jurors vote before hearing arguments?
- **Final split:** How did they vote at the end?
- **Vote changes:** Which jurors changed their minds and why?
- **Gaps logged:** What evidence did jurors wish they had?

## Key Rules for the Jurors

1. They must follow the law exactly as the judge states it
2. They can only use evidence from the case file
3. They can't know about the real trial or look up information
4. They vote alone at first (so nobody influences anybody)
5. They must explain what would change their mind
6. They can't vote just to go along with the group

## What Makes This Useful?

Running many trials shows:
- How often juries vote guilty vs. not guilty
- Which pieces of evidence matter most to different jurors
- How jurors' personalities affect their votes
- What evidence is missing that jurors wanted
- How long it takes juries to agree

It's like running 30+ versions of the same trial with different juries to see what happens.

## For the Curious: How Are Jurors Different?

Each juror is intentionally different. The script:
1. Starts with a balanced set of personality traits
2. Randomly shuffles each trait across the 12 jurors
3. Checks that no traits are too similar to each other (mathematically)
4. Saves the result so the trial is fair and comparable

This means if you run the trial with the same juror panel twice, they should reach the same verdict (because it's based on evidence, not randomness). But different panels might vote differently based on their personality mix.

## Need Help?

- **To understand the case better:** Read `case-requirements.md`
- **To see how jurors think:** Look at files in `.claude/agents/jurors/`
- **To see past trial results:** Check `verdicts.md`
- **To understand the legal standard:** Read `jury-instructions.md`
