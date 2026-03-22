---
title: 'Automating Workflow on Datasources'
description: "Sitecore's Datasource Workflow Action solves one of the trickiest workflow problems: making sure component datasource items get approved along with their parent pages."
pubDate: 2025-11-15
---

[Part 1](/blog/first-post/) covered Basic Workflow and why it matters. If you set that up, you likely ran into a problem quickly: your page items go through workflow, but the datasource items powering your components do not.

This is a real operational problem. A content author can approve a page, publish it, and find that the hero banner or promo component shows stale content because the datasource item was never approved.

## The datasource approval gap

When you build pages in Sitecore with component-based rendering, content often lives in two places:

- The **page item** itself (metadata, navigation title, page-level fields)
- **Datasource items** that components reference for their actual content

If workflow is only applied to page templates, datasource items can be created and edited without ever going through an approval step. Editors do not always understand the underlying architecture. They approve the page and assume everything is ready to publish.

## The solution: Datasource Workflow Action

Sitecore ships a workflow action called **Datasource Workflow Action** that solves this automatically. You attach it to a workflow command on your page workflow, and when that command fires, it cascades the workflow state change to all referenced datasource items.

Setup takes four steps:

1. **Create the action** on the workflow command where you want the cascade to happen. For most implementations, this is the final approval command.
2. **Set the Datasource Workflow Command** field to point at the equivalent approval command in your datasource workflow.
3. **Configure the scope** — Self, Children, or Descendants, depending on your content architecture.
4. **Test before going to production.** Validate that datasource items actually advance when you approve a page.

## Where to put the action in multi-stage workflows

If your page workflow has multiple review stages (editor → legal → brand → published), attach the Datasource Workflow Action to the **final approval command only**. This lets pages move through their staged review process normally, while datasources flip to approved in one step when the page is finally cleared.

Content authors do not need to know any of this is happening. They approve the page, the action fires, and all the component content comes along for the ride.

## Platform support

The Datasource Workflow Action is available across Sitecore XM, XP, and XM Cloud. If you are on an older platform, check the Sitecore documentation for version-specific configuration details.

Next up: [Part 3](/blog/third-post/) covers how to change workflow states programmatically when you need more control than the out-of-box actions provide.
