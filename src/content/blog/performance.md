---
title: 'Does Performance Even Matter?'
description: 'AI agents could automate tedious workflow validation tasks in Sitecore, but is the processing overhead worth it? A look at the cost question through the lens of historical technology adoption.'
pubDate: 2025-12-07
featured: false
---

I recently attended a Frontend Masters workshop: Building an AI agent from Scratch, by Scott Moss.  I had just finished writing my Sitecore workflow series, and the Workflow section of the course made me wonder if there's any need for the kind of information I just spend a good amount of time researching and writing.

## The idea

Sitecore workflows support custom actions that fire when an item moves between states, or prevent an item from publishing if it doesn't pass certain validation checks.

An AI agent can do all that, but can do a whole lot more. Instead of just checking to make sure the alt text is present, it can make sure it's a meaningful description, and not just image123.jpg. 

Add to that, once the agent exists, it becomes a lot easier to modify & configure.  Typically these things are run with text instructions written the way that you'd describe them to a human. 

"ContentIntro is a required field and shouldn't be more than a few setences."

"RelatedEvents should have 3-5 selections, and an event should not be related to itself."

Setting that up on its own in Sitecore involves a pretty thorough understanding of Workflow structure and how validation actions work. 

There's only one advantage to doing workflow I can think of:

## Performance 

A simple rule-based action checking if a required field is empty takes... IDK maybe a few bytes of processing?  Is "bytes" even the right term here?

...googles...

Ok no. But my point is generally right.  It's minimal CPU Cycles, and it's done in nanoseconds. 

Compare that to an AI agent scouring the page doing the same analysis. If you're comparing that to even simple AI prompts, the compute spend is increased by measures of thousands, even with simple prompts. Explaining why [OpenAI spends millions of dollars responding to Please & Thank You](https://www.vice.com/en/article/telling-chatgpt-please-and-thank-you-costs-openai-millions-ceo-claims/).

For a content team publishing hundreds of items a day, that overhead multiplies.

## Does it matter though?

Given that AI can catch things that the typical actions can't, the question that popped into my head was:

"Is the tradeoff worth it?"

And I did not have to think about that for long, because I think the answer is obviously yes.  Even if the alt-text example was the ONLY advantage, it's absolutely worth the few thousand nanoseconds to think about it.

The real question I have, that I don't know the answer to:

Is it worth supplementing that AI agent with a few regular workflow actions to save a bit on compute?  If that alt text is missing entirely, don't bother sending the agent until it's fixed.

Is that going to even make a dent on anyone's balance sheet?

I kinda doubt it.

So I guess I've got the next logical post in that blog series of mine.
