---
title: 'PowerApps Portals Project Ramp-Up: Project Management'
date: 2019-11-10T20:00:00.000Z
description:
  Power Apps Portals projects have their specifics when it comes to project
  management. Read this blog post and learn from my best practices that shall be
  considered to run a robust project management practice.  
categories: ["Portals"]
tags: ["Project Management"]
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
# tl:dr

**(1)** When choosing the project management tool chain, consider enablement of collaboration within your Portals team and outside your team with other project teams. There will always be an intersection.

**(2)** Consider ways to document your Portals configuration, so they can be traced back - both functionally and technically.

**(3)** Create your test data in advance and let it be reproducible in every environment.

**(4)** When running an agile project, consider the ability to independently deploy anytime.

**(5)** Train involved project staff about Power Apps Portals right form the beginning as this will reduce time and efforts during project delivery.

**(6)** Do not underestimate efforts for the transition to operations after a the project ends.

![](/img/portals-project-management.jpg)

Now let's deep dive into depicted specifics of project management in Power Apps Portals projects.

# Methodology

Every project shall follow some sort of defined methodology; may it be the one of your choice. When comparing those methodologies, consider your way to an efficient collaboration model. Most likely, your Portals project will be accompanied by other projects, e.g. for development of the core application that your customer will use to do business. Often the Portals project is much smaller than the core project in terms of staff and budget. Still, your Portals project is equally important as this is probably the forefront for the customers of your customer, i.e. the people, your customer drives business with. So choose your collaboration model wisely as there will be joint efforts, such as business process design or changes to CDS schema. If those project teams are not regularly synchronized, the project will not as smoothly as required. In my projects, it has proven to be efficient to have at least one functional consultant in each of the separate project teams. Those consultants inform and dispute about requirements of every team and eventually conclude to a consensus that drives a more effective solution. As a side benefit, knowledge is shared across project teams and unavailability of team members can be covered to a certain extent. 

Once your collaboration model has been selected, do your research on the most effective yet easy tool chain for your collaboration processes. Azure DevOps Services from Microsoft deliver great value in project teams of small and large scale. It is important to enable each project member right from the beginning to be able to find, complete & document their work items. Another key area to be covered is an intuitive way to collaborate on work items within your Portals project and outside with other project teams. Think about how to document test cases and how to  track the execution of those.

# Requirements

Traceability of requirements, decisions and solution components is key to a robust project management. At any point of time, may it be during or after the project delivery, you must be able  to recall those work items artifacts. I favor to leverage the concept of user stories for functional and technical requirements documentation. The functional part of the user story will be formulated by the businesses and describes the expected outcome to achieve an anticipated value. In that same user story, I always note down the technical side of how the outcome is achieved. That could be the name of a configuration artifact (e.g. Web Page, Entity Form Metadata or piece of JavaScript) or the required CDS schema (e.g. form, view or flow). On that same user story, important decisions are being noted down, too. Being able to track back when and why this artifact was put into place can be a huge time saver and quickly answers endless discussions at a a later point in time - potentially to people, who will join the project later.

# Deployment

Try to find a way to coordinate with the deployment processes of other project areas. Potentially, the core project deployments will consist of CDS schema. Chances are high that your deployments may only consist of Portals configuration, which is CDS data - so your regular schema deployment process may not be able to deploy your latest and greatest features. Keep a tight and regular communication to those who are in charge of the deployment process and inform about the specialties of your Portals solutions. Maybe even consider to have a dedicated deployment pipeline just for your Portals project.

# Training

As mentioned, specific Portals training will greatly reduce friction in your Portals projects. Your developers, which may have a more traditional Dynamics 365 background, will benefit from knowledge about how the Portals framework is doing its job. Clear all the question marks beforehand, maybe before each development iteration. For instance, teach them where JavaScript shall be injected and how it is supported with data by Liquid on your Web Page. Also consider to train your test team at an early stage, so they can test at full pace once deployment is done. It can be frustrating to you and to them, if they don't know how to login to your Portal or why processes look different to those in your model driven app on CDS.

# Bug-Fixing

Consider to safeguard team capacity for bug-fixing activities alongside of the regular requirements delivery. I have seen project phases where a single bug caused so much effort that planned deployments had to be postponed. This often happened where developers shared work across project areas and their skills were scarce among the whole project.

# Maintenance

So you delivered the project with your team to fullest satisfaction. Your developers, testers and customer representatives know the solution inside-out and have got to known the Portals framework deeply. Now the solution will transition to regular operations and the first bug can not only cause catastrophe, but maybe even diminish the acceptance for your solution by the decision makers of your customer. Remember to train support staff. Show them how the solution works and what components are critical to your solution. Give guidance on how to tackle a problem occurring in Portals. They might have not ever heard of Portals and are now in duty of giving support for your solution. Show them the standard means of troubleshooting and give access to your requirements documentation, so they are able to follow up, which of the component is relevant to the problem. Consider to involve them at an earlier project stage, so they can share their requirements for professional maintenance and support in the long run.

*****
