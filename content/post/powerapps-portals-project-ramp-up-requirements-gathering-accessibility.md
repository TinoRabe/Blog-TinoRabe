---
title: 'PowerApps Portals Project Ramp-Up: Requirements Gathering (Accessibility)'
date: 2020-01-07T06:00:38.877Z
description:
  This post will give insights on requirements for accessibility, which are
  specific to PowerApps Portals. Use this compilation of best practices in your
  requirements gathering process before the project starts and during project
  delivery.
categories: ["Portals"]
tags: ["Accessibility"]
author: "Tino Rabe"
showToc: true
TocOpen: true
draft: false
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

> ![Accessibility](/img/requirements_accessibility.jpg "Accessibility")

During the requirements gathering process, it will be useful to put yourself in the shoes of the Portal users. Know your Portal users and tailor your Portal solution specifically to create an effective solution and drive user adoption. 

 **Service Consumption** \
Take this as a bad example for misconceived consumption of a Portal solution:
The Portal gives rich information via entity lists with useful filtering and searching. Unfortunately, the exposed  lists have more than 20 columns and the majority of users (at least 80%) use the Portal from a mobile browser on their smartphone. Now such wide entity lists can easily become unusable or the filter area becomes to big. Another example are pictures, which are optimized for the desktop client, but do not scale down well enough when accessed on a mobile device. 

 **Color Scheme** \
Another area of great accessibility is an acceptable color scheme. Maybe the customer requests the adherence to some corporate identity color scheme, which makes content hard to read. Also consider your requirements gathering in terms of color scheme for a guided user experience as well. Have important information to show? Make it standout from the not-so-important information by applying a meaningful colors that will not mislead the Portal user and captures user attention usefully. Also consider font style and font size to present content to the audience in an appropriate manner.

**JavaScript: Browser Support** \
It can be best practice to define the set of browsers you aim to support with your solution. You do not want to run critical business logic on web pages with custom client-side scripts, which are not being executed by the browsers of your user base. Consider your user base and maybe state supported browsers in a dedicated Portals FAQ, so users are not left frustrated through unnecessary intransparency. Another way to overcome this shortcoming would be a well-designed JavaScript solution, which informs the user as soon as incompatibility is detected (e.g. dedicated alerts or remarks). In a later post, I will share some best practice on how to monitor the Portal service health towards detected browser exceptions on client-side by leveraging Azure Application Insights.

***
