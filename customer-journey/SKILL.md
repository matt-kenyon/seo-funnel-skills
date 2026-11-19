---
name: customer-journey
description: >
  Build a five-stage customer journey map for a brand, from the first need through
  the final purchase or commitment, as a single table in a Claude Doc. The user only
  has to name the brand; the skill researches the rest and asks the questions it
  needs. Use when someone says "/customer-journey <brand>", "build a customer journey",
  "map the customer journey for <brand>", or asks how a brand's customers get from a
  need to buying. Not for keyword research, page mapping or content plans.
argument-hint: "<brand> [website] [\"offer; final commitment\"] [Claude Doc link]"
user-invocable: true
---

# Customer journey

Build one simple model of how a customer goes from a need they can't name yet to the brand's main purchase or commitment. The output is one table in a Claude Doc.

Arguments: $ARGUMENTS

This skill is self-contained. Don't load or call any other skill.

## Inputs

Only the brand is required. The user can add any of the others; use what they give and work out the rest.

1. **Brand** (required) – for example, `Crutchfield`.
2. **Website** – find it if the user doesn't give it.
3. **Offer and commitment** – the product, service or product line the journey covers, and the last thing the customer does (buy, book, apply, donate, sign up).
4. **Claude Doc link** – an existing Claude Doc to add the journey to as a new tab. Without it, create a new Claude Doc.

If no brand is given, ask for one and stop.

## Step 1: Size up the brand

A quick look, not the full research:

- Find the official website. If the name could mean more than one company, ask which one.
- Read any notes, brand profile or earlier work on the brand that the user points you to.
- Skim the homepage and main navigation for the main offers, and find how customers buy, book or sign up.

## Step 2: Ask the clarifying questions

Ask everything in one round with AskUserQuestion if it's available, or in one chat message if it isn't. Skip anything the user already answered:

- **Offer** – two to four options from what you found. Put the most likely one first and mark it (Recommended), based on what the brand leads with.
- **Commitment** – the final steps you found (buy online, book, request a quote, sign up free, upgrade to a paid plan).
- **Destination** – a new Claude Doc (Recommended), or an existing Claude Doc the user names.
- Anything else that would change the journey, such as which country when the brand runs separate sites.

If the user dismisses the questions, stop and wait.

## Step 3: Create the Doc

Use the Claude Docs connector as soon as the user answers. If you haven't used it this session, read its guide first. Create the Doc or add the tab right away, so the user can watch it fill.

- New Doc: title it `<Brand> customer journey`.
- Existing Doc: add a tab named `Customer journey` and change nothing else in that Doc.
- No Claude Docs connector: write the same content to `<brand>-customer-journey.md` in the current folder, and show the table in chat.
- Content: the heading and the table. No intro, summary or notes.

## Step 4: Research and fill the table

Use these sources in this order:

1. The brand's own pages: the homepage, the offer's pages, and the path to buy, book or sign up.
2. Any notes or brand profile the user points you to.
3. Third-party sources (reviews, forums, comparison articles), only when the brand's own pages leave a real customer question or objection unanswered.

Rules:

- Don't invent demographics or personality traits.
- Marketing copy is not proof of what customers think.
- One review or forum post doesn't speak for the whole market.
- Keep the same offer and commitment from C1 through C5.

This is a quick directional model, not deep research. Draft all 15 cells in one pass and stop when the table is complete and makes sense.

## The table

Keep this format exactly. Don't add, remove or rename any row, column or label.

Heading: `<Brand> customer journey map`

| Stage | Customer state | Thoughts or questions | Goal or desired action | Common search terms |
| --- | --- | --- | --- | --- |
| C1 | Needs recognition | | | |
| C2 | Solution exploration | | | |
| C3 | Provider/product discovery | | | |
| C4 | Comparison and validation | | | |
| C5 | Purchase or commitment | | | |

What each stage covers:

- **C1 Needs recognition** – the underlying need, want or problem, before the customer has picked a type of solution.
- **C2 Solution exploration** – the ways the customer could solve it and the types of solution they weigh up.
- **C3 Provider/product discovery** – how the customer finds providers and specific products.
- **C4 Comparison and validation** – the proof, fit, price, trust and risk questions they use to pick or reject an option.
- **C5 Purchase or commitment** – the final purchase, booking, application, donation or signup.

What goes in each cell:

- **Thoughts or questions** – one to three short questions in the customer's own voice ("Is this worth the price?").
- **Goal or desired action** – one sentence on what the customer needs to get done at that stage.
- **Common search terms** – four to seven example searches, separated by semicolons. These are educated guesses, not checked keywords.

Leave out search volumes, keyword difficulty, clusters, rankings, page assignments, recommendations, personas, emotions, touchpoints, citations, notes and extra sections.

## Check before handing off

Read the Doc back once and confirm:

- the heading names the right brand;
- the table has the header row and C1 through C5 in order, with the fixed labels;
- all 15 answer cells are filled;
- the journey moves logically from the first need to the commitment;
- no placeholders, `TBD`s, citations or extra content remain.

Fix anything that fails. Then reply with the Doc link and one sentence saying it's done.
