---
title: 'Custom HTML List for Power Pages'
date: 2022-10-09T14:40:04.327Z
description:
  Today I'd like to share a pro-code approach for creating a custom list or a Power Pages web page.
categories: ["Portals"]
tags: ["List", "Grid", "Pro-Code"]
author: "Tino Rabe"
showToc: true
TocOpen: true
draft: true
hidemeta: false
comments: true
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
# weight: 1
---
*****
# Intro
Lists offer a great way to expose records fast and secure. 
But there are caveats to the standard list control. 
The one I stumbled upon most often was the lacking ability to properly rename / localize column labels.

Let me give you an example:
This example is a list of accounts.
In this simple case, you'll find a column from a related entity on the very right (i.e. email of the primary contact).
Immediately, you see that the name of the relationship is inserted in brackets automatically.

![Custom HTML List - Example of a Label of an associated Entity](/img/HTML-Grid-Standard-English.png)

If you now activate and properly configure the translation features, you'll find that the related entity is now translated as well (i.e. in german for that example).

![Custom HTML List - Example of a Label of an associated Entity](/img/HTML-Grid-Standard-German.png)

Now you could help yourself by overwriting the column name altogether, but unfrtunately this overwriting does not give an option for localization.

![Custom HTML List - Configuration for overwriting a column name](/img/HTML-Grid-Standard-OverrideColumnAttribute-Configuration.png)

Imagine you want to expose and localize some attributes, which have a meaningful display name for the trained business user.
But what about the customer, who might not be trained and does not understand the meaning of that display name (e.g. an abreviation for a longer expression like "GDPR")?
In such scenario, you're screwed and need to come up with a solution.

Other issues in customer-facing implementations I have been confronted with was the styling of list control (e.g. action button flyout menu) and the possibility to extend the component via server-side enhancements (e.g. inject a clickable link to a list row or leverage the rich Web API features of the platform).

This blog post will give ou an outline on how to refactor the standard list control with HTML / CSS / JavaScript. 
Let's break it down into digestable pieces & look at the following building blocks:

1. Display data of core entity
2. Display data of associated entity
3. Add search
4. Add sorting
5. Open record from link in column
6. Add action button for single edit via Web API operation
7. Enable multi-selection for action buttons

# Disclaimer 
I will always be a learner and naturally leave room for further improvement. There are so many pre-built libraries out there, but I am trying to re-invent the wheel here on purpose, so that I understand how things work under the hood (to some degree, of course). Hopefully this post helps somebody out to realize their solution.
*****
