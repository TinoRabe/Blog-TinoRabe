---
title: 'PowerApps Portals Project Ramp-Up: Requirements Gathering (Scope)'
date: 2019-11-25T18:00:43.148Z
tags: ["test3"]
categories: ["test3"]
description: >-
  This post will give insights on requirements documentation and scope, which
  are specific to Power Apps Portals. Use this compilation of best practices in
  your requirements gathering process before the project starts and during
  project delivery.
categories: ["Portals"]
tags: ["Scope"]
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
> ![Scope](/img/requirements_scope.jpg "Scope")

# Functional
The scope of your Power Apps Portals project defines what and how requirements will be delivered. It will also give reference on how success is defined and what acceptance means.
The first pillar of a resilient scope management practice is to think about your requirements from a functional point of view. Those requirements are typically formulated together with the business stakeholders. Functional requirements shall describe what value is added to the solution. It could be something like 'As a Portal user, I want to login with my existing Microsoft account so I do not have to remember a separate pair of credentials exclusively to the Portal'.

# Technical
The technical requirement specification defines how the desired value is realized from a system point of view. Those technical requirements can be documented and tested by test cases separately. In my experience, it is sufficient to make the technical requirement a part of the functional one, e.g. by splitting the user story into a functional and a technical part. So in the example above, the user story is enhanced with a technical spec, e.g. 'External login to be implemented via Azure AD B2C identity provider for all external users (building blocks: Azure AD B2C identity service incl. branding, Portal site settings)'. This will also have the benefit of a documentation on where to look into for troubleshooting of a specific functionality.

# Targets
Consider targets as the motivation or the guidance in your functional requirements specification. Those shall describe the ROI (Return of Investment) and why this is relevant to the solution. Adding this to our exemplary user story could be something like: 'Leveraging an existing Microsoft account as primary login improves usability and reduces administration/training efforts in comparison to local login'.

# Non-Targets
The non-targets shall not describe the negation of the formulated target, but rather the limits of the targets. It will help the reader to further understand the core of the target. A non-target could also describe the conditions to not meet the ROI. Take this example in our user story: 'Leveraging identity providers other than Microsoft is not required as 90% of our users have a Microsoft account'.

This is what our exemplary user story could look like by now:

![User Story](/img/requirements_userstory.jpg "User Story")

# Acceptance Criteria
An acceptance criteria is usually formulated within the test case. It describes the expected result out of a defined action. Consider this to be a crucial point in your requirements gathering process as it will define how your solution artifacts are accepted by the customer. From customer side, they can be used to describe the critical conditions under a functionality is considered to be functional at its core. An example test case for our user story could be:

![Test Case](/img/requirements_testcase.jpg "Test Case")

# Quality Gates
This certainly is not a must have, but best practice. A quality gate defines the availability of a critical building block of your solution, especially as it can have a dependency to subsequent building blocks. In our example this could be 'External authentication working and tested as expected'.

***
