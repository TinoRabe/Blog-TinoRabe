---
title: 'Custom dialog with Bootstrap modal for Power Apps Portals'
date: 2021-12-21T14:40:04.327Z
description:
  Today I'd like to share a pro-code approach for creating a custom dialog leveraging Bootstrap modal for a Power Apps Portals web page.
categories: ["Portals"]
tags: ["Dialog", "Pro-Code"]
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
Power Apps Portals already give great functionality in terms of dialogs out of the box. You will find them when creating or editing a record from a list or from a form.

But what if you do not use an list or form, but still you do want to show a dialog for a certain use case? Thanks to the concept of custom Web Templates and some frontend development (HTML / CSS / JavaScript) this is achievable. Such approach can become a useful component for other pro code Portals solutions.

This blog post will give an example on how to make this possible.  
Let's break it down into digestable pieces:

1. Concept
2. Build a custom modal and call it from a custom button
3. Input submit incl. progress handling and success output
4. Closing and refreshing
5. Input validation

# Concept
I'd like to start with a User Story, so that the scope is somewhat defined:  

***As a Portal user, I want to click a button "Contact Me", so that I can submit a contact request with my email and some feedback text***

As a next step, I recomend to do a mockup for UI vaidation prior to implementation. 
Here is my example:  

![Bootstrap dialog mockup](/img/dialogs_bootstrap_mockup.png)

This leaves us with the following building blocks:  
- Entity to store our input in Dataverse
- Web Page with a custom Page Template
- Page Template with a custom Web Template

Our core functionality is hosted in our custom Web Template, so let's outline the solution artifacts of the Web Template.
- **button** to open the modal (incl. CSS to style the button)
- **modal header**
  - **title** to name the dialog
  - **close button** to close the modal from the upper right corner
  - **CSS** for styling the header
- **modal body** 
  - **input field** for email
  - **input field** for feedback text
  - **CSS** for styling the body
- **modal footer**   
  - **submit button** to call the WEB API for submitting the input to Dataverse
  - **reset button** to destroy all input
  - **CSS** for styling the footer
  - **CSS** for styling the loading message
  - **CSS** for styling the error message
- **JavaScript** (functionalities)
  - input validation to check for entered email expression incl.
  - submit input to Dataverse via WEB API (incl. lookup to logged-in Portal user and originating record)
  - show loading message after input submit
  - show success message after input submit to Dataverse
  - error handling: show error message when input submit to Dataverse fails
  - reset input fields after click on **reset button**
  - close modal when data submit succeeded & after 10 seconds

# Addendum
It is alo quite easily possible to inject our custom functionality into a Web Page directly without utilizing a custom Web Template. Simply copy the custom code into the HTML source field of the Web Page record and you are good to go.

# Disclaimer 
I will always be a learner and naturaly leave room for further improvement. There are so many pre-built libraries out there, but I am trying to re-invent the wheel here on purpose, so that I understand how things work under the hood (to some degree, of course). Hopefully this post helps somebody out to realize their solution.
*****
