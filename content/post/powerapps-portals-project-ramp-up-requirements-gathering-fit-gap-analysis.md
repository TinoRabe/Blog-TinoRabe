---
title: 'PowerApps Portals Project Ramp-Up: Requirements Gathering (Fit-Gap Analysis)'
date: 2020-01-20T07:00:00.000Z
description: 
  This post will give insights on requirements documentation and scope, which
  are specific to PowerApps Portals. Use this compilation of best practices in
  your requirements gathering process before the project starts and during
  project delivery.
categories: ["Portals"]
tags: ["Requirements"]
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

> ![Fit-Gap Analysis](/img/requirements_fitgap.jpg "Fit-Gap Analysis")

So let's look at some best practices on how to identify requirements and also some considerations on how to document them. 

# Portals Standard vs. Requirements  
You're up to a good start if you know the Portal functionality very well. And this is template specific, if a template is used. If you leverage the customer self-service template, deep-dive into the template specific Web templates of the solution. If you know all the templates and their unique features, it will be a lot easier to not only choose the right template for your customer needs, but also shape your solution architecturally with out-of-the-box features. Consider to categorize the gathered requirements into at least three categories:

* Standard functionality without customization
* Standard functionality with customization
* Custom functionality

This can make life easier when it comes to comprehend estimated efforts and also maintains a first class documentation of your solution. Put yourself in the shoes of the support staff after the project phase. Wouldn't it be nice to know straight away that a buggy feature is relying on standard functionality? That will make troubleshooting so much easier as reproduction in other (vanilla) environments can be carried out right away.

# Proof of Concepts / Prototyping
Looking at my past engagements, I tend to do at least little PoCs for all the requirements that fall into the category ‘Custom Functionality’ and often also ‘Standard functionality with customization’ if they are critical to the success of the solution. Those PoCs often help to drive an efficient presales phase for high level requirements. If you can generally show the technical feasibility of the solution, your customer is more likely to choose you as the trusted adviser. 
The Portals frameworks suggests ease of configuration for lots of kinds of requirements. And don’t get me wrong: these possibilities DO enable exactly this and outcomes will be able to be realized the majority of cases with quick time to market. Once you leave the boundaries of the framework, the project can be become quite complex easily. I came to the conclusion, that business requirements often share similarities among different engagements. Hence, you can recycle your PoC knowledge here to enable even quicker turnaround times -may it be in other PoCs or simply in answering questions to shape an effective solution for your customer.

All of the PoCs can eventually conclude to a (working) prototype. Sometimes it is useful to aim for a prototype to be the first deliverable in the first phase of a project. Once this phase is successfully achieved, the key pillars of the prototype can be refined in iterations consecutively, which will ultimately conclude in the final solution.
Furthermore, your learnings out of this prototype phase may resolve in the discovery of requirements being infeasible or impractical – partially or in general. Again, a great mechanism to do the so important estimation of efforts/time for later project phases.

# Required Libraries
Here is a real-world example for a learning out of a prototype:
The customer aimed to compose a dashboard for the Portal user, that exposes charts of various kinds. Of course, the native integration of PowerBI was demonstrated in a PoC. The customer declined on this approach as it did not meet the requirements. After this, we did another PoC and leveraged the standard chart integration of the framework via liquid tags. It was a much simpler solution and the customer was interested again. Still, there were some shortcomings at the time, which had to be overcome. So at the end, custom JavaScript chart libraries had to be evaluated in terms of feasibility and licensing.

This simplified example does not only demonstrate the importance of PoCs/prototypes, but also made me aware that a PowerApps Portal project always is a web development project. Customers are users of the internet and have some experience of what is impossible or simply have seen interesting, dynamic functionalities in other web-based applications. No wonder those functionalities are then expected to work in PowerApps Portals as well – maybe even out of the box. And with some JavaScript, that can be the case. This does not stop at JavaScript libraries, but can also be CDS solutions from ISVs and so on. So if you aim to leverage 3rd party libraries, pay attention to licensing and technical constraints as well as the support model.
If you do this upfront as part of the fit-gap analysis, you can accomplish your requirements gathering process with confidence.

# Automation
In your fit-gap analysis, pay close attention to required automation functionalities, which typically will be realized via Power Automate (Flow) or custom plugins. Take some time to understand the desired degree of process automation and challenge this well. Form my personal experience, customers tend to automate as much as possible once they come to realize the powerful capabilities of the platform. It shall not be about quantity, but about quality. 
Sometimes a good user training can be much more effective yet cost-reducing in comparison to an automated solution, which needs to be developed/tested/supported. Hence, keep a close eye on the ROI the requested automation artifact.

***