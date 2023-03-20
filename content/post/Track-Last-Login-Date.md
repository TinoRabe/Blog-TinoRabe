---
title: 'Track Last Login Date - a Pro-Dev Solution'
date: 2023-03-18T22:27:00.327Z
description:
  Today I'd like to share a pro-code approach for tracking the last successful login date of a logged-in user. This solution has become required as the former standard solution is deprecated.
categories: ["Portals"]
tags: ["Liquid", "JavaScript", "Pro-Code", "User", "Login", "Logging", "Content Snippet"]
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
# Intro
Back in the days of Adxstudio, we were able to track the last successful login date of a user by simply leveraging a standard functionality.
Years later (2018), this functionality has become deprecated and is no longer available.
That means, the Site Setting "Authentication/LoginTrackingEnabled" will not have any effect.
In a customer-facing project, this functionality has become necessary as the customer would like to report on user accounts, who have not logged in for a considerable amount of time.

This blog post will give  a solution on how to refactor the standard functionality by utilizing some Liquid in liaison with the fantastic Web API capabilities of Power Pages.
Let's break it down into digestable pieces & look at the following building blocks:

1. Create a Content Snippet with the custom code
2. Inject Content Snippet

Feel free to make use of this approach in your Power Pages solution :-)

# Create a Content Snippet with the custom code (Tutorial)
I have chosen to house the logic in a Content Snippet for the following reasons:
1. Reusability as a Content Snippet can easily be injected wherever required.
2. A Content Snippet is language-aware, so the functionality can be aligned with local GDPR requirements.

Content Snippets are traditionally used when you want to display a label or larger pieces of text content in liaison with localization. HTML and JavaScript are typically organized in a Web Template.
So you could also organize the logic within a custom Web Template and not in a Content Snippet as demonstrated here.
 *The result will be the same.*

The solution design considers when and where the custom script is executed.
In my case, the Content Snippet is injected into the the Web Template "Home".
In consequence, the Web API operation is only sent to the browser, whenever the Last Successful Login Date is different than the current browser date. And this evaluation is done server-side as it is implemented via Liquid code. If a patch is really required, the custom script is sent to the browser client-side.

So if the User logged in for the first time, the target column is patched once. If the User revisits the Web Page again on that same day, no further patch is required.

To make it even more lightweight and a bit more resilient, let's also check if the current Portal user is authenticated or anonymous. The logic shall only be executed for the authenticated user.

Prior to writing the first line of code, I always like to approach the solution with a design upfront.
Please find this design enriched with the relevant artifacts of the final solution.

In this solution, the standard column "adx_identity_lastsuccessfullogin" will be utilized, but you could use any date/time column.

**(1)** Enable Web API

* Enable entity "contact" for usage via Web API via Site Setting 

* Enable entity attribute "adx_identity_lastsuccessfullogin" for usage via Web API via Site Setting

**(2)** Create custom logic in a new Content Snippet:

* Create new custom Content Snippet with a traceable name, e.g. "Customization/Contact/DocumentationOfLastLogin", & place custom server-side script (liquid) in combination with client-side script (Web API) in this Content Snippet

* With Liquid, check if the current Portal user is authenticated; only continue if this checks returns 'true'
```HTML
{% if user %} 

<!--
The Liquid object "user" is utilized; if the user is not authenticated, value 'null' will be returned.

Find out more about the Liquid object "user" here:  
https://learn.microsoft.com/en-us/power-pages/configure/liquid/liquid-objects#user

-->
{% endif %}
```
* With Liquid, get current server time and extract date w/o time 
```HTML
{% assign today = now | date : 'd' %} 

<!--
The Liquid date filter 'd' is utilized, so that the queried date is shortened to the 'short date pattern'; essentially, only the date w/o the timestamp is filtered as I only want to compare dates and not times;

Find out more about date filters here:  
https://learn.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings#table-of-format-specifiers
-->
```
* With Liquid, get column "adx_identity_lastsuccessfullogin" of table "contact"and extract date w/o time 
```HTML
{% assign lastSuccessfulLogin = user.adx_identity_lastsuccessfullogin | date : 'd' %} 

<!--
As this solution only aims at logged-in users, the Liquid object "User" can be leveraged, i.e. the column can be queried directly.

Again, the date is filtered.
-->
```
* With Liquid, compare both times (i.e. dates): if they do not match, then patch column "adx_identity_lastsuccessfullogin" with current date via Web API
```HTML
{% if today <> lastSuccessfulLogin %}

<!-- 
We only want to run the logic if the user logs-in at another day than what is saved to the contact record.

Although a Liquid date filter for ISO 8061 is available as per standard, it did not work as expected in my case (ref: https://learn.microsoft.com/en-us/power-pages/configure/liquid/liquid-filters#date_to_iso8601).
So I ended up refactoring this conversion with JavaScript, which proves to work as expected.

The actual PATCH operation via Power Pages Web API is rather standard.
A little twist is the query of the GUID of the logged-in Portal user.
Again, this is realized by leveraging the user object of Liquid.
Find more about the PATCH operation via Power Pages Web API here: https://learn.microsoft.com/en-us/power-pages/configure/write-update-delete-operations#basic-update
-->

    <script type="text/javascript">

        {% comment %} Initialize current Date in ISO 8601 format {% endcomment %}
        
        var time = new Date();

        var dataObject={

            "adx_identity_lastsuccessfullogin": time.toISOString()
        };

        $( document ).ready(function() {

            webapi.safeAjax({

                type: "PATCH",

                url: "/_api/contacts({{user.id}})",

                contentType:"application/json",

                data: JSON.stringify(dataObject),

                success: function(res) {

                    console.log(res)

                }

            });

        });

    </script>

{% endif %}
```
**(3)** Add new Content Snippet to existing Web Template

```HTML
{% include 'snippet' snippet_name:'Customization/Contact/DocumentationOfLastLogin' %}

<!--
Place it in a useful Web Template or Web Page.
In my case, it has been placed on the Web template "Home" as this Web Page will be loaded after the user logs in.
-->
```
# The Content Snippet in final shape.

```HTML
{% comment %} Variables {% endcomment %} 

{% assign today = now | date : 'd' %} 

{% assign lastSuccessfulLogin = user.adx_identity_lastsuccessfullogin | date : 'd' %} 

{% if user %}

    {% if today <> lastSuccessfulLogin %}

        <script type="text/javascript">

            {% comment %} Initialize current Date in ISO 8601 format {% endcomment %}
            
            var time = new Date();

            var dataObject={

                "adx_identity_lastsuccessfullogin": time.toISOString()
            };

            $( document ).ready(function() {

                webapi.safeAjax({

                    type: "PATCH",

                    url: "/_api/contacts({{user.id}})",

                    contentType:"application/json",

                    data: JSON.stringify(dataObject),

                    success: function(res) {

                        console.log(res)

                    }

                });

            });

        </script>

    {% endif %}

{% endif %}
````
# Disclaimer 
I will always be a learner and naturally leave room for further improvement. I am trying to re-invent the wheel here on purpose, so that I understand how things work under the hood (to some degree, of course). Hopefully this post helps somebody out to realize their solution.

I'd like to thank [Nikita Polyakov](https://www.linkedin.com/in/nikitapolyakov/) for some valuable feedback on this blog post, which led to some improvements.
*****
