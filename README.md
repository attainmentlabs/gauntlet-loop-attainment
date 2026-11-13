# Gauntlet Loop (Attainment)

A Claude Code skill that polishes an existing draft until it beats a real reference. A builder improves each part, and a separate critic compares it blind against the reference until ours wins. Hard time and round limits are built in.

What it adds to the original method:
- How to pick a bar that is named, fetchable and comparable
- A second test each round: a panel of six readers from one audience, scored from round 0
- Field lessons from real runs on emails, posts, charts, app screens, specs and flows

## Install

```bash
git clone https://github.com/attainmentlabs/gauntlet-loop-attainment
cp -r gauntlet-loop-attainment/skills/gauntlet-loop-attainment ~/.claude/skills/
```

Then say "gauntlet loop this" with a draft and a reference.

## Credits

- Method: Matt Shumer, who named the Gauntlet Loop while building [Claude of Duty](https://github.com/mshumer/Claude-of-Duty) ([original prompt](https://github.com/mshumer/Claude-of-Duty/blob/main/prompt.md), [guide](https://somethingbig.ai/gauntlet-loop))
- Bar-picking guidance adapted from [robonuggets/gauntlet-loop](https://github.com/robonuggets/gauntlet-loop) by Jay E at RoboNuggets (CC BY 4.0). Changes: shortened, reworded, and combined with the guards and panel method below.
- Guards, panel method and field lessons: Attainment Labs

## License

CC BY 4.0. See LICENSE.
