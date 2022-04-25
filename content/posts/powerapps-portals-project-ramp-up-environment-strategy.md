---
title: 'PowerApps Portals Project Ramp-Up: Environment Strategy'
date: 2019-11-04T05:00:00.000Z
description:
  Learn how to structure your environment in dependency of the Portals project
  type. I will share best practices that I have come across based on actual
  experience from customer-facing Portals projects. This post will give pros and
  cons for individual environmentstrategies. Build knowledge to reflect, consult
  and decide on the environment strategy today to drive a professional Portals projects. 
categories: ["Portals"]
tags: ["Environments"]
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

> tl;dr

**(1)** Best Practice: Scale environment strategy in dependency to project scale (e.g. enterprise project, small-medium sized project, etc.)

**(2)** Best Practice: Consider at least two groups of stakeholders: You and your customer

**(3)** Best practice: Try to avoid a single-portal approach

**(4)** Best practice: Have your environment strategy strategy in place before the actual requirements delivery starts

> Preamble

This is my personal take on a resilient environment strategy strategy. Still, there are many opinions about this out there, so hopefully you can take some benefits out of it for your personal environment strategy strategy. This post will not discuss about the technical setup of an environment strategy. Please look at it from a strategic point of view and than choose your favorite tools and system setups to support that strategy.

> environment strategy - Introduction

In my years as a functional consultant, I have come worked in projects of different scale:

* Enterprise Business
* Small-Medium sized Business
* One Man Business

Almost in every project, the environment strategy strategy led to some discussion in the beginning of the project. In their essence, these discussions and considerations are not particularly unique to PowerApps Portals projects, but rather to software delivery projects in general. Still, I always bring this topic up in the very beginning of the project and too often the environment strategy strategy has not been considered deep enough by the customer. Hence, I feel this is a crucial factor to a healthy project. This is my personal opinion among many opinions out there. Microsoft has just released a [guidance for efficient environment setup strategies on the Power Platform](https://powerapps.microsoft.com/en-us/blog/establishing-an-environment-strategy-for-microsoft-power-platform/) themselves - give it a read and maybe find a model in between that works best for your project. Let's start with projects at enterprise scale. Here's a sample illustration, which should not be anything new to you:

![environment strategy Enterprise](/img/alm-enterprise.jpg "environment strategy Enterprise")

Now let's deep dive into each pillar of the scale at enterprise setup:

1. **Sandbox:** Use a dedicated sandbox instance to explore the framework features **for yourself being the ISV**. Not only explore them, but test them until you break them (from a technical or from a requirements perspective). Use such sandbox to build confidence and become an expert for certain areas/features of the framework. A dedicated sandbox is also great to conduct proof of concepts (PoCs) before delivering requirements in the DEV environment. At any point consider to push a customization or even a copy from your DEV environment to Sandbox, to have a more realistic base for your PoCs.
2. **DEV (Development)**: Typically, this is where the requirements are delivered. Once a requirement is delivered, a unit test along some regression testing shall be executed by the implementing team in this environment. Consider how to package solution artifacts, so you can deliver and develop them independently from on another. DEV shall always be the only environment, where you make actual customization, such as schema or configuration changes for your PowerApps Portal. All subsequent environments should only be supplied with customization via deployments and ideally should not be done manually.
3. **TEST**: Deploy your customization and let your internal test team perform the same unit tests along some regression testing. Maybe your project requires some integration with 3rd party systems - that is a great environment to test those integrations and to learn by the progress you are making, so the final integration with productive data can run as smoothly as possible. In some projects, it might even be useful to have a dedicated STAGING environment between DEV and TEST. STAGING can give you several benefits, e.g. the possibility to check how your continuous integration process is working or the possibility to pack transport solutions by merging solution artifacts from DEV in STAGING for further deployments.
4. **QA (Quality Assurance)**: Analogous to TEST, delivered requirements will be tested here. In contrast though, the customer will be the testing party this time. Invite relevant testing stakeholders to this environment and gather their feedback. Examples: functional requirements, such as features or user experiences, can be tested by the business. Critical security mechanisms and features can be tested by the IT. Reports and dashboards can be tested by management representatives. Consider QA to deliver training to your customer and maybe let the customer train their user base by themselves in QA.
5. **PROD (Production)**: Once all your deliveries have been accepted by the customer, you deploy from QA to PROD. A required integration routine of 3rd party system data will run smoothly as you have tested it upfront in TEST ( maybe in QA). Now you see your solution in action and hopefully, enjoy the ROI (Return of Investment) your solution is giving to your customer over the time :-) You should never make changes to PROD directly. If a bug is identified, you will reproduce it in QA, TEST and DEV, before you start fixing it.

![environment strategy SMB](/img/alm-smb.jpg "environment strategy SMB")

Let's look at a environment strategy strategy for SMB businesses, which may not require such a full-blown setup as the project staff might be essentially smaller. This strategy also distinguishes between the ISV and the customer. Key difference is that both share the DEV environment for individual purposes.

1. **DEV (Development)**: Again, this is where your requirements delivery happens, i.e. customization & configuration. Once that has completed and everything is unit tested, the development process will be frozen and no changes will be made in DEV. Now the customer does his testing and training, eventually. This might even be done as a joint effort as project staff may be small, so you help out the customer in testing and training. Helping in training does not necessarily mean that you test your customization on your own, but rather guide the customer and explain the changes, so he can test it right away and give feedback directly. Same goes with training, where you either take the lead in training or you stand aside of the customer to answer questions along the training and/or take feedback from the end users. This environment strategy strategy is working fine for me in the SMB market. It profits from quick response times, quick time to market times and a simplified environment strategy (less environments to handle, less deployment efforts and less people to talk to).
2. **PROD (Production)**: Once all your deliveries have been accepted by the customer, you deploy from DEV to PROD. Form what I have seen, data integrations are rare and if they are needed, they will be performed in PROD directly. This keeps efforts low and feedback loops short. Now you see your solution in action and hopefully, enjoy the ROI (Return of Investment) your solution is giving to your customer over the time :-) You should never make changes to PROD directly. If a bug is identified, you will reproduce it in DEV and also fix it in DEV. 

![environment strategy No Project](/img/alm-no-project.jpg "environment strategy No Project")

Last but not least there is what I call the 'No Project' environment strategy strategy, wich consists of a single instance to do it all. I am sure, everybody knows that this is not a desirable strategy, but I have worked in projects where the customer explicitly agreed to the risks involved and 'dictated' this strategy. I highly recommend you not to go down this path. The customer may argument that another instance my drive costs and that this may not give essential benefits to the solution. This argumentation falls short if you look at the sunken costs if just any bug/training/customization has to be dealt with along the daily production operation and something goes just slightly wrong. Technically, it is possible to mimic a dedicated/separated area in a PowerApps Portal by leveraging various security mechanisms.  This approach is usually requested by very small customers, e.g. one person company, from my experience. Still, I always try to convince them to have at least a dedicated DEV environment. I expect these discussions to become obsolete with PowerApps Portals from now on in contrast to Dynamics 365 Portals ([see licensing blog post for reference](https://tinorabe.com/post/powerapps-portals-project-ramp-up-provisioning-licensing/)) - we'll see about that.
*****
