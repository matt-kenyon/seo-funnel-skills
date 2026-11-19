---
name: topical-themes
description: >
  Find a brand's topical themes and score them so you know which SEO funnel (topic cluster) to
  build first. Finds themes of four types (business differentiators, product or service features,
  pain points the brand solves, and topics it wants to be known for), scores each from 1 to 5 on
  business value, expertise and demand, and writes a ranked table to a Claude Doc the user can edit.
  Use when someone says "/topical-themes <brand>", "find topical themes", "prioritize topical
  themes", "score my themes", "which cluster should I build first", or asks what topics a brand
  should build content around. Not for keyword research on single articles or for writing content.
argument-hint: "<brand> [website] [customer journey Doc link] [Claude Doc link]"
user-invocable: true
---

# Topical themes

Find the topical themes a brand could build SEO funnels around, score each one, and say which to
build first. A topical theme is the core idea a cluster of 7 to 10 pieces is built around, and it
leads readers to something the brand sells.

The result is one ranked table in a Claude Doc. The user can change any score.

Arguments: $ARGUMENTS

This skill is self-contained. Don't load or call any other skill.

## Inputs

Only the brand is needed. Use anything else the user gives.

1. **Brand.** A name and website, or a pasted business summary. Use the summary for a new or
   made-up brand. If the user says the brand is made up or has no website, treat the summary as
   the brand's own pages and don't search for the brand.
2. **Customer journey (optional).** A Claude Doc link or a pasted table showing how customers go
   from their first need to buying. Use its first stage for pain points and its search terms as
   starting points for demand.
3. **Claude Doc link (optional).** An existing Doc to add the themes to as a new tab. Without
   one, create a new Doc.

If there's no brand, ask for one and stop.

## Step 1: Research the brand

Find the answers yourself first, so the user only has to confirm or correct them. Keep it to about
15 to 25 pages or searches in total.

- **The brand's own pages.** Read the homepage, the main product or service pages, the pricing
  page and the about page. Note:
  - what the homepage leads with
  - what each page sells
  - how customers buy, book or sign up
  - every claim the brand makes about itself
- **Its most valuable offer.** The offers that get the most space on the homepage and in the main
  menu are usually the ones worth most to the business.
- **Its edge over competitors.** Search the brand's main category to find two or three
  competitors. Then check the brand's most specific claims one at a time: does each competitor make
  the same claim on its own site? Search for the competitor's name with the claim if you need to.
  A claim no competitor makes is the brand's likely edge. A claim that competitors share isn't.
  Note any proof that backs the edge, such as the brand's own page ranking for that topic, or
  forum posters recommending the brand for it.
- **What customers ask.** Search the brand's reviews (Trustpilot, Google, industry review sites),
  Reddit and forums about its category, and its own FAQ or Q&A pages. Note the three or four
  questions buyers ask most, and anything they praise or complain about.
- **A topic to own.** Pick the topic where the brand's edge meets the questions customers ask most.

## Step 2: Confirm your findings with the user

Show the user what you found and let them confirm or correct it. Their answers make the scores
more accurate, because they know things your research can't find, such as margins, sales calls
and plans.

Use AskUserQuestion if it's available. It holds four questions at a time, so ask the four brand
questions in one call. If you need the keyword tool question, ask it in a second call straight
after. Without AskUserQuestion, ask everything in one chat message. Skip any question the user's
input already answers.

In every question, put your research-backed answer first and mark it (Recommended), so the user
can accept it with one click.

- **Most valuable offer.** "Which offer matters most to the business?" Give two to four offers
  you found as options.
- **Edge.** "I found these claims that competitors don't make. Which can you back up?" Make it
  multi-select. Put the claims your research found unique first, and name the competitors you
  checked. Add "None of these". The user can type in anything else, such as their own data,
  credentials, a process or customer results.
- **What customers ask.** "Reviews and forums suggest customers ask these most. Is that right?" Make
  it multi-select, with the questions you found as options.
- **Topics to own or avoid.** "Is there a topic you want to be known for, or one to leave out?"
  Offer the topic you picked as the first option.
- **Keyword tool.** Ask this only if a keyword research tool is connected (Surfer, Ahrefs, Semrush
  or similar): "Should I use <tool> for search volumes? It may use credits."

If the user says to use your research, or asks you to choose, go with your recommended answers
and say what you went with in your final reply. If the user skips the questions, do the same, and
say which scores rest on your research alone.

## Step 3: Create the Doc

Use the Claude Docs connector as soon as the user answers. If you haven't used it this session,
read its guide first. Create the Doc with only the heading, so the user can watch it fill.

- **New Doc:** title it `<Brand> topical themes`.
- **Existing Doc:** add a tab named `Topical themes` and change nothing else.
- **No Claude Docs connector:** write the same content to `<brand>-topical-themes.md` in the
  current folder, and show the table in chat.

## Step 4: Find the themes

Aim for 8 to 15 themes, usually two to four of each type. If a type doesn't fit the brand, use
fewer of it.

| Type | Where to find it |
| --- | --- |
| Business differentiator | What the brand does differently, from its messaging and the user's answers |
| Product or service feature | The main products, services or features on its pages |
| Pain point | The problems that send customers looking. Use the customer journey's first stage if you have it, the brand's pages, and forum or review threads about the category |
| Topic to be known for | The subjects the brand wants authority on, plus the basic education its buyers need before they can choose |

A topic the user wants to be known for becomes a theme, even if your research didn't turn it up.
Leave out any topic they want to avoid.

Every theme must pass these checks. Merge or drop any theme that fails one.

- **It leads to something the brand sells.** Name that page in the table. If the brand has no
  page for it yet, write "None yet".
- **It can hold 7 to 10 pieces across the buying journey.** "Itchy skin and food allergies" is a
  theme. "Best dog food" is a single article. "Dogs" is too broad.
- **It doesn't overlap another theme.** If two themes would answer mostly the same questions, merge
  them.
- **It uses the customer's words.** Name it the way buyers would describe it.

## Step 5: Score each theme

Give each theme a score from 1 to 5 in three columns. Each score is relative to the other themes
on this list. Use the full range: if every theme gets a 4, the scores can't help anyone choose.

**Business value: if this theme brought in customers, how much would that be worth?**

| Score | Meaning |
| --- | --- |
| 5 | It leads straight to the brand's most valuable offer, such as the main product, a recurring plan or the highest-priced service. |
| 3 | It leads to a smaller product, an add-on or a secondary service. |
| 1 | It has no clear path to anything the brand sells. |

Raise the score by 1, up to 5, when the theme leads to the offer the user named as most valuable,
when the brand's messaging pushes that offer hardest, or when the user wants to be known for the
theme.

**Expertise: can the brand say something here that competitors can't?**

| Score | Meaning |
| --- | --- |
| 5 | The brand has proof competitors lack, such as its own data, a unique product or process, credentials or customer results. |
| 3 | The brand knows the topic well, but competitors say much the same thing. |
| 1 | Anyone could write it, and nothing ties it to this brand. |

Base this on the edge you found in Step 1 and on the user's answers. A claim found only in
marketing copy counts for less than proof the user confirms or proof you found yourself, such as the
brand already ranking for the topic or customers recommending it on forums.

**Demand: are people actually asking about this, in Google, in AI or on sales calls?**

| Score | Meaning |
| --- | --- |
| 5 | Many people ask about it. Search results are full of dedicated pages, and forums and Q&A sites keep asking it. |
| 3 | Some people ask. A few dedicated pages and threads come up. |
| 1 | You find little sign anyone asks. |

To check demand, run one or two web searches per theme, using the words a buyer would type. If a
search tool hits its rate limit, switch to another one. Look at:

- whether the top results are pages written for that exact question
- whether forums, Reddit or Q&A sites keep asking it
- what related questions show up

The same real questions are what people ask AI tools. If the user confirmed that customers ask
about it on sales calls or in support, raise the score by 1, up to 5. Don't add the point for
questions you found only on forums, because the searches already count those.

If the user agreed to a keyword tool in Step 2, add search volumes for each theme's top two or
three searches and name the tool in "Why these scores".

**Total and order.** Add the three scores together, for a total out of 15. Sort the table from the
highest total to the lowest. If two themes tie, put the one closer to a purchase first. A theme
that leads to the main offer, or that covers the comparison and pricing questions buyers ask just
before they buy, counts as closer.

## The Doc

Heading: `<Brand> topical themes`

Then one table, sorted by total:

| Theme | Type | Page it sells | Business value | Expertise | Demand | Total | Why these scores |
| --- | --- | --- | --- | --- | --- | --- | --- |

- **Theme.** The theme's name in the customer's words.
- **Type.** One of: Business differentiator, Product or service feature, Pain point, Topic to be
  known for.
- **Page it sells.** The product, category, service or landing page the cluster would lead to.
- **Why these scores.** One or two short sentences giving the evidence behind all three scores.
  For example: "It leads to the main meal plans. Competitors say the same thing. Owners keep
  asking about it on Reddit."

Under the table, add these three lines and nothing else:

1. `Start with: <top theme>.` Follow it with one sentence on why.
2. `Demand scores are estimates. Check the searches in a keyword tool before you write.`
3. `To change a score, edit the table and ask Claude to update the totals and order.`

Leave out search volumes unless a keyword tool supplied them. Don't add keyword lists, article
ideas, cluster maps or any other sections.

## Check before handing off

Read the Doc back once and confirm:

- the heading names the right brand
- every theme has all eight columns filled
- every total equals its three scores added together
- the table is sorted by total, and any ties are broken as described in Step 5
- the scores use the full range, with no column of nearly identical numbers
- no two themes overlap
- no placeholders or "TBD"s remain

Fix anything that fails. Then reply with the Doc link, the top three themes and their totals, and
any score that rests only on your own research because the user skipped a question.

## When the user changes a score

If the user edits scores and asks for an update, add up the totals again, re-sort the table, and
update the "Start with" line if the top theme changed. Change nothing else.
