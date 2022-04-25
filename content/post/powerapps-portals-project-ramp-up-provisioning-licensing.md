---
title: 'PowerApps Portals Project Ramp-Up: Provisioning (Licensing)'
date: 2019-10-30T06:00:46.488Z
description:
  In this post you will advance your knowledge around considerations for
  choosing the right license for your customers, so you can ramp-up your
  PowerApps Portals project with confidence.
categories: ["Portals"]
tags: ["Licensing"]
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

# tl;dr

**(1)** Recap: PowerApps Portals are licensed differently to Dynamics 365 Portals

**(2)** Recap: PowerApps Portals are licensed via a consumption model (i.e. number of authenticated logins & number of unauthenticated page views)

**(3)** Recap: Dynamics 365 Portals are licensed via an availability model (i.e. number of provisioned instances)

**(4)** Best Practice: Consider leveraging Dynamics 365 Portals in transition period for more efficient pricing in some scenarios today

**(5)** Best Practice: Consider self-hosted Community Portal for evaluation in larger project teams

# Licensing of PowerApps Portals

As of the publishing date of this post, there a great differences among the possibilities to license your Portal implementation. Here is a simple illustration, which might help you understand your options:

![Licensing Comparison](/img/licensingcomparison.jpg "Licensing Comparison")

As outlined in my previous post ([PowerApps Portal Templates](https://tinorabe.com/post/portals-provisioning-template-licensing-advanced-techniques-to-master-powerapps-portals/)), you are able to provision your portal in a: 

* **PowerApps Portal**: PowerApps environment **without** Dynamics 365 model-driven apps
* **Dynamics 365 Portal**: PowerApps environment **with** a Dynamics 365 model-driven apps

In this first post regarding templates, I have not written about a third option for any new Portal implementation. [That is the Community edition of Portals.](https://github.com/Adoxio/xRM-Portals-Community-Edition)

The Community edition of Portals is an open-source version of the Portal framework. Historically, Microsoft was kind to publish a certain version (v8.x) of the framework after Adxstudio was acquired and the framework was made available as an add-on application to your Dynamics 365 environment. Naturally, the framework for Dynamics 365 Portals has evolved since then, but the Community edition shall not be forgotten in any of your considerations. So if you are looking to get your hands on the framework and maybe host it on Azure, you can absolutely do that. The Community edition comes wit a MIT license. Still pay attention to potential hosting costs, so your calculation of running costs is accurate.

Ok, let's have a look at the different pricing models for PowerApps Portals by Microsoft. I am counting Dynamics 365 Portals into that same bucket, as frontiers are blending and the actual product (= provisioned Portal) does not differ from one another in functionality).

First off all and as of today, PowerApps Portals are licensed differently to Dynamics 365 Portals. That means, if you provision a PowerApps Portal from a PowerApps environment without a Dynamics 365 model-driven app, your Portal will be licensed by consumption. 

Essentially, that means the following for PowerApps Portals w/o Dynamics 365 apps:

1. If you provision a PowerApps Portal, you will be entitled to use it with any internal user, that is licensed to use PowerApps.
2. If you want external users to login to your PowerApps Portal, they will be considered as authenticated external users.
3. If you want external users to consume you PowerApps Portal content, that is not secured via authentication, they will be considered as unauthenticated external users.

Pricing for mentioned capacity add-ons of PowerApps Portals are listed here: [PowerApps and Microsoft Flow licensing FAQ](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-powerapps-portals-licensing) and in the [current licensing guide](https://go.microsoft.com/fwlink/?linkid=2085130).

Furthermore, that means the following for Dynamics 365 Portals with Dynamics 365 apps:

1. Once an applicable threshold of required Dynamics 365 licenses in your tenant is met, you are entitled to a single Dynamics 365 Portal. 
2. The public access to this Portal (unauthenticated & authenticated) does not need to be licensed via capacity add-ons in the same way as PowerApps Portals need to.
3. Any additional Dynamics 365 Portal will be licensed by instance, not by consumption.
4. There are some other restrictions for certain kind of authenticated users, so study the licensing guide carefully.

Pricing for additional Dynamics 365 Portals instances are listed here: [PowerApps and Microsoft Flow licensing FAQ](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-powerapps-portals-licensing) and in the [current licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409). 

Your calculations must be accurate as this kind of Portals provisioning my drive costs by the number of required instances. So in a full fletched Portals project at enterprise scale, you will need multiple Portals instances for a resilient Application Lifecycle Management (ALM) setup. I will share some further best practices on ALM in a later post.

# Transition Period for Dynamics 365 Portals

As of today, there is a transition period, so both Portals types (PowerApps Portals & Dynamics 365 Portals) live side by side. Hence, it is still possible to provision a Dynamics 365 Portal today (i.e. after 1st October 2019), that will not need any capacity add-on for authenticated/unauthenticated users). Simply by leveraging a Dynamics 365 model-driven app in your PowerApps environment. When this transition period will end, is not transparent to me. How the existing Dynamics 365 Portal licenses will be transitioned to PowerApps Portals capacity model after that period, is also not transparent to me. But I will give an update in this post, once I gained clarity.

Remarks:
**Big thanks and kudos** to the following MVPs, who answered my questions upfront towards the co-existence between mentioned Portals license schemes:

* Mark Smith ([Twitter](https://twitter.com/nz365guy))
* Nick Doelman ([Twitter](https://twitter.com/readyxrm))
* Jukkan Niiranen ([Twitter](https://twitter.com/jukkan))

*****