# SEO funnel skills

These are the two Claude skills I used in the Surfer Academy video [How to Build an AI SEO Funnel That Actually Makes Money](https://youtu.be/fOMpmY8-RbE).

| Skill | What it does |
| --- | --- |
| `customer-journey` | Maps how a brand's customers get from their first need to buying, in five stages (C1 to C5), as one table. |
| `topical-themes` | Finds a brand's topical themes and scores each from 1 to 5 on business value, expertise and demand, so you know which SEO funnel to build first. |

Run `customer-journey` first. You can then give its table to `topical-themes`, which uses it to find pain points and starting searches.

## Install in Claude (web or desktop app)

1. Download `customer-journey.zip` and `topical-themes.zip` from this repo.
2. In Claude, turn on code execution in Settings > Capabilities, then go to Customize > Skills.
3. Click "+", then "Create skill", then "Upload a skill", and upload one zip. Repeat for the other.

## Install in Claude Code

Copy the `customer-journey` and `topical-themes` folders into `~/.claude/skills/`. Then type `/customer-journey <brand>` or `/topical-themes <brand>`.

## Where the results go

Both skills write their table to a Claude Doc when the Claude Docs connector is available. Without it, they save a Markdown file and show the table in chat.
