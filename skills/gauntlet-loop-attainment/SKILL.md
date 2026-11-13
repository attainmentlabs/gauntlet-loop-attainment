---
name: gauntlet-loop-attainment
description: Run a Gauntlet Loop (a builder plus a separate blind critic) to polish an existing draft until it beats a real reference. Use when the user types /gauntlet-loop-attainment, says "gauntlet loop", "run a gauntlet on this", or "polish this until it beats X". Picks a real bar, writes the prompt, runs it with a hard time and round cap, and reports a before and after. Works for posts, emails, images, app screens, specs and flows. Not for first drafts.
---

# Gauntlet Loop (Attainment)

The Gauntlet Loop method is by Matt Shumer (original prompt: github.com/mshumer/Claude-of-Duty/blob/main/prompt.md, guide: somethingbig.ai/gauntlet-loop). The bar-picking guidance is adapted, shortened and reworded from Jay E's gauntlet-loop skill at RoboNuggets (github.com/robonuggets/gauntlet-loop, CC BY 4.0). The guards, the panel method and the field lessons below come from Attainment Labs' own runs in November 2026.

## Why the guards exist
- Uncapped loops run for many hours and can use a whole weekly plan limit. Always cap.
- A blind win against a weak reference proves nothing. The loop is only as good as its bar.
- Started from nothing, a loop polishes toward the wrong look. Start from a draft that is already on brand.

## Step 1: Check it is ready
Ask only what is missing, in one message:
1. **What are we polishing?** A finished draft: file, page, deck, preview link. No draft: say so and offer a normal first pass instead.
2. **Which brand?** Load its guide. The critic must reject anything off guide.
3. **The bar:** a real reference better than ours today. Never "make it perfect". No bar given: offer 2 or 3 candidates, one line each, recommend the hardest one you can actually fetch, and wait for a pick.
4. **Cap:** default 60 minutes or 5 rounds, whichever comes first. The user can raise it. Never run uncapped.

## Picking the bar
A bar must be:
- **Named:** one specific thing ("Stripe's pricing page"), never a category ("award-winning sites").
- **Fetchable:** the critic can get the real thing. Compare against the real thing, never a description of it.
- **Comparable:** the two can sit side by side and a judge can pick one.

| Work | Bar that works |
|---|---|
| Website, app screen | A named best-in-class live page or app, same viewport |
| Writing, posts, emails | A specific published piece for the same reader, same length and format |
| Code, tooling | A named repo, plus its tests or benchmark as the measurable half |
| Research, analysis | A named analyst report or paper, judged on rigour and coverage |
| Deck, document | A real deck or doc from a firm known for it, same page count |
| Video, visual | Real footage or screenshots from a named shipped piece |

- Pick a reference written for the SAME reader. A famous piece for a different reader loses round 0 and proves only the floor.
- For one-to-one writing (a client email, a direct message), the best bar is the writer's own approved, already-sent note that got a reply.
- If there is a number to beat (load time, word count, pass rate), add it next to the reference. Taste plus a number beats taste alone.
- If only a weak bar exists, say so. Treat round 0 as a floor check, then judge every later round against the previous round's winner.

## Step 2: Write the prompt (show it to the user before running)

```
TASK: Improve [thing] at [location]. Keep [brand] exactly: [colours, fonts, voice rules, banned words]. Do not change [facts, prices, claims, legal lines].

METHOD: You (the lead) split this into small parts yourself. For each part, one builder sub-agent improves it, and a SEPARATE critic sub-agent that has not seen the builder's notes compares ours against [reference], labels hidden, and answers only "A better" or "B better" plus the single biggest gap. If the reference wins, the builder fixes that gap and the critic judges again. The critic is harsh; praise is useless. It also fails anything that breaks the brand guide.

BAR AND STOP: Stop a part when the critic picks ours blind. Stop everything at [cap], even if not finished. At the end, give me a before and after side by side and a list of what changed. Never publish, send, merge or deploy.
```

Keep it short: no architecture, file layout or part list unless the user asked. Critic rules: binary verdict, not a score; never sees the builder's reasoning; compares against something external.

## Step 3: Run it
- The lead runs it with helpers: one builder plus one critic per part, parts in parallel.
- Track time and rounds. Stop at the cap.
- Copy the best round to the project folder as you go. Scratch folders do not survive a restart.

## Step 4: Report
Before and after side by side, what changed, rounds and time used, which parts still lose, and the winner's weakest line as the remaining weak spot. Show everything that ships with the piece (a link card, an attachment), not only the words.

## The two-test method (what made runs work)
A blind A or B win alone often did not earn the owner's yes. Every round gets two tests:
1. **Blind judges:** three fresh critics, new against previous best, labels swapped for one so position does not decide it. Five numbered lines: verdict, biggest gap, weakest part of the winner, one question on the user's open complaint, fails for both.
2. **A reader panel:** one named helper holding six readers of the ONE audience you pick, scoring 1 to 10. Resume the same helper each round so scores compare. Score the current draft first as round 0. Ask for each reader's weakest element, the fix three share, the single change, and the ceiling.

Keep a round only if it wins both tests. When they split, report both and let the user choose.

### Setup files (one scratch folder)
- **context.md:** writer, reader, what is being answered, and a "DECIDED, may not change" list of the user's standing choices.
- **rules.md:** lettered fails built from the brand rules and the user's own complaints. Ask judges to list fails for BOTH versions; those lines are the next round's fix list.
- **builder-brief.md:** the only allowed facts, must-have elements, the user's notes word for word, real samples of the voice.

### Rules learned
- **Pick one audience.** One piece rarely wins two panels. Choose, then score every round with that panel.
- **A judge's opinion is not a test.** Turn any suggested fix into its own blind pair before building on it. Ideas every judge loved have lost 3 of 3 once tested.
- **Price the user's own requested lines** instead of dropping them: score the base, base plus line one, base plus both in one panel call, and report what each line costs. Let the user decide.
- **When every judge names the same weak line,** make that one edit and label it untested.
- **Check facts before the panel sees anything.** Builders drift: softened claims become absolute, credits shift to the wrong person. Readers punish a slightly wrong credit more than a missing one.
- **Read the real source first.** Read the actual thread, live code, real screens or published piece before writing round 0. A baseline written from memory had to be corrected after four judged rounds.
- **Feed round 0's "single change" straight into round 1.** Writer helpers' own candidates often lost to the two the lead built from that line.
- **Judges flip on small wording between rounds.** Do not chase it. Settle the line on the fixed rules and mark it untested.
- **Close with a separate fact and brand check** on the final: does anything mislead, does anything break a rule, does silence on part of the original message read as rude.

## By kind of work

**Short emails and messages**
- Panel for a one-person audience: the SAME reader in six moments (on the phone between meetings, comparing on price, liked a rival, hates being chased, tired late in the day).
- What lost: "following up", tallying what was already sent, "is this still worth pursuing", naming a rival's strength, stock praise, a tidy sum-up closer, any line about the sender's own growth.
- What won: open on news the reader cares about, one concrete step in the reader's own words, a closing question that names the choice, a two-item menu plus "or something else" that can be answered in one word.

**Posts and short comments**
- Search the platform's own post links for a same-reader reference. Record link, counts and date.
- A short line has little room for proof, so expect a lower ceiling.

**Images and charts**
- Judges look at the rendered file at phone size (about 469 px wide).
- Wins came from text size and one plain punchline line, not new art.
- A number the reader must see "from the picture alone" has to sit inside the picture as well as the headline.
- When polishing stalls, start again blank: build three very different rough concepts, pick by the one-look test, then polish the winner.

**App screens**
- Free teardown articles carry real screens of category leaders. Render them to the same width as ours.
- For two versions of the same screen, tell judges where to look, or they judge the whole screen and split at random.
- Measure tap sizes and clearances each round so a round cannot quietly break them.

**Specs and flow plans**
- Check the live code and the research before writing the spec; the real change can be much smaller than assumed.
- The best judge line for a spec: "questions a builder would ask". For a flow: "the one moment where the most people are lost, and why".
- Panel: designer, developers, growth lead, two new users with different reasons, the CEO.
- Label every research number verified or unverified, and add an off switch with an owner when evidence runs against a decision.

**Drafts where the user dictated the lines**
- List their lines as decided and add a fail letter for dropping any. The loop polishes only the wording inside them.
- Price a version that breaks a decided line, so the user sees what their line costs without the loop overriding them.
