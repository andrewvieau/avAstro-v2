---
title: 'Sitecore Workflows that Work'
description: 'A practical introduction to Sitecore workflows: what they are, why teams skip them, and how to get started with the Basic Workflow without the headache.'
pubDate: 2025-11-01
---

If you are working with Sitecore content, you have probably heard about workflows. You may have even been told to set them up. But in many implementations I have seen, workflow gets deferred until after launch, then quietly forgotten.

That is a shame, because workflow is one of the best things Sitecore does out of the box.

## What is a workflow?

A workflow is a series of predefined states that a piece of content must pass through before it can be published. Each state functions as a checkpoint. In a simple two-state workflow, content moves from **Draft** to **Approved** before it can go live. Nothing is published by accident.

The benefits are real:

- **Prevents accidental publishing** of incomplete or unapproved content
- **Creates accountability** by requiring an explicit approval action before content goes live
- **Auto-versions on edit** when configured correctly — editors working on approved items get a new draft automatically, protecting the live version

## So why does workflow get skipped?

Usually it comes down to launch pressure. Teams are moving fast, stakeholders want to see content live, and adding an approval step feels like friction. Sometimes an organization already has an external review process — email chains, spreadsheets, legal review portals — and adding a Sitecore layer feels redundant.

The other issue is inconsistent application. If workflow is only applied to some templates and not others, editors run into unpredictable behavior and start working around it.

## The quick-start approach

The fastest way to get value from workflow is to start with **Basic Workflow**, which Sitecore ships out of the box. It has exactly two states:

1. **Draft** — content is being edited
2. **Approved** — content is ready to publish

There is one command connecting them: an Approve action. That is it. No rejections, no email notifications, no multi-stage review. Just a gate that prevents anything from going live without an explicit approval.

You can apply Basic Workflow to a template in minutes by setting it in the template's standard values. Once it is in place, editors will see an approval button in the ribbon when they are ready to publish.

How do you know workflow is not in place? If content becomes publishable immediately upon creation with no approval step, it is not configured. Check the standard values for your page templates and look for the `__Workflow` field.

## What comes next

This is the first post in a three-part series on Sitecore workflows:

- **Part 1** (this post): Overview and foundational concepts
- **Part 2**: [Automating workflow for datasource components](/blog/second-post/)
- **Part 3**: [Modifying workflow states programmatically via code and GraphQL](/blog/third-post/)

If you are starting from scratch, deploy Basic Workflow first, get your team used to the approval step, and then layer on automation and API control from there.
