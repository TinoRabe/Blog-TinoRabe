---
title: 'PowerApps Portals Project Ramp-Up: Requirements Gathering (User Management)'
date: 2020-01-06T06:00:00.000Z
description: >-
  This post will give insights on requirements gathering for the user
  management, which are specific to PowerApps Portals. Use this compilation of
  best practices in your requirements gathering process before the project
  starts and during project delivery.
categories: ["Portals"]
tags: ["User Mgmt"]
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
> ![](/img/requirements_user-management.jpg)

# User-In
A crucial aspect to an effective solution for the Portal users is the user-in process. This will likely be the first touch point and therefore the first impression those users will have. From my experience, the customer has a clear picture of which functionality the Portal has to cover. But the user experience from 'click one' is ever so often neglected. This becomes especially true if the Portal aims to be a self-service Portal. Consider the following questions for your requirements gathering:

* Which method of user registration shall be realized (self registration, prepared invitation, requested invitation, provisioning of credentials upfront, registration via federation with external identity providers)?
* How will relevant Web Roles be applied (manually, automatically)?
* What happens after the first successful login, e.g. to which web page will the user directed and which information is exposed/demanded?
* Is it useful to send a follow up email separately after the first login (e.g. suggest guidance via documentation/help area/demo/videos/etc.)?
* Who and when shall monitor the completion of open invitations?
* What is the threshold of failed login attempts and what are the next steps, maybe even automated?

# User-Out
Another area to pay attention to are requirements to the user-out process. This time it is not so much about user experience, but rather important to the management of data quality and integrity.
Here are some questions for guidance:

* Shall it be possible to open the possibility to request an user account deactivation/deletion?
* If an user account is no longer active, what shall happen with assigned records (e.g.open cases or open activities)?
* Who and when shall monitor user accounts that have not logged in for a defined periods of time, e.g. have not logged in for more than 12 months)?
* Is it necessary to leverage the functionality to have users locked out after a certain attempt of failed logins?

# User Support
The last area in user management that I would like to share my best practices on is the user support. A first class user support can be a game changer and drive user adoption massively. Imagine a self service portal, which is designed to be intuitive, but leaves the majority of users puzzled for some of the core functionalities. Or that they regularly experience bugs/malfunctions in their everyday usage. Hence, here are some questions to drive the requirements gathering:

* How and where shall the user be able to report bugs/malfunctions? 
* What does the user experience in the resolution/feedback process look like?
* Where and how does the user request for help within the Portal?
* Can it be useful to leverage the forums area to enable user to help each other?
* Can it be useful to expose some of the knowledge articles just for Portal usage topics?
* Can a virtual agent be leveraged to reduce support efforts?
* How is the effectiveness of the Portal evaluated?

***