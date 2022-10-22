---
title: 'Custom HTML List for Power Pages - Display data of core entity'
date: 2022-10-22T14:40:04.327Z
description:
  This is the first part of the blog series about custom HTML lists for a Power Pages solution.
  It describes the fetch of the required data of the core entity in Dataverse.
categories: ["Portals"]
tags: ["List", "Grid", "Pro-Code"]
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
# Build FetchXML statement
Let's start with querying the data now.
The core entity (a.k.a. 'table') is 'Accounts' (account) and as we want to refactor the standard list from the intro blog post, we will need the following attributes (a.k.a 'columns'):
- Account Name
- Main Phone
- Address 1: City

![Advanced FInd to built FecthXML statement for download](/img/HTML-Grid-Fetch-Account.png)

The downloaded FetchXML statement shall look like this for this example:

```xml
<fetch mapping="logical">
  <entity name="account">
    <attribute name="name" />
    <attribute name="telephone1" />
    <attribute name="address1_city" />
  </entity>
</fetch>
```

# Host FetchXML statement in custom Web Template incl. unit test
Now we will create a new Web Template record and insert the FetchXML in there.
Remember to utilize the appropriate Liquid tags for FetchXML.
Last but not least, let's check if our query actually deliveres the expected results.
The quickest way is to enhance the created Web Template by some JavaScript, so we can output the fetched data to the console.
For this example, the code looks like this:

```html
{% comment %} Data Provider {% endcomment %} 
{% fetchxml fetch_accounts %}
<fetch mapping="logical">
  <entity name="account">
    <attribute name="name" />
    <attribute name="telephone1" />
    <attribute name="address1_city" />
  </entity>
</fetch>
{% endfetchxml %}

{% comment %} Unit Test {% endcomment %}
<script>
  console.log ("FetchXML Result for Account")
  console.group ("Account Details")
  {% for account in fetch_accounts.results.entities %}        
      console.log ("{{account.name}}")
      console.log ("{{account.telephone1}}")
      console.log ("{{account.address1_city}}")   
  {% endfor %}
  console.groupEnd()
</script>
```

![Web Template to host FetchXML statement](/img/HTML-Grid-Fetch-Account-WebTemplate.png)

# Result
Now create a Page Template record to host our custom Web Template and just use this Page Template in a Web Page.
As we are logging to the console of the browser dev tools, the result should look something like this:

![Web Template to host FetchXML statement](/img/HTML-Grid-Fetch-Account-UnitTest.png)

Very good, we have successfully queried the account data form Dataverse by custom code.
In the next blog post, we will take this a step further and query the primary contact of the account, which means querying data from an associated entity.

# Disclaimer 
I will always be a learner and naturally leave room for further improvement. There are so many pre-built libraries out there, but I am trying to re-invent the wheel here on purpose, so that I understand how things work under the hood (to some degree, of course). Hopefully this post helps somebody out to realize their solution.
*****
