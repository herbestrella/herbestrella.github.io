---
layout: post
title: add-google-analytics-to-chirpy-github-page
date: 2023-12-18 12:00:00 -500
categories: [github,github-pages,chirpy,google-analytics]
tags: [github,github-pages,chirpy,google-analytics] # TAG names should always be lowercase, separated by commas
---

# Goal

Pretty simple and self explanatory, there's a section on the _config.yml for Chirpy that allows you to add google analytics. I've never used Google Analytics before and I thought it would be neat get some insight from the page.

## Google Analytics for Beginners

I found [Google Analytics Training](https://analytics.google.com/analytics/academy/course/6) after I successfully implemented it, that's how easy it is to setup.

## Setup Analytics

Browse to the [Sign-up](https://accounts.google.com/ServiceLogin?service=analytics), you'll need a google account to get started. I just used my personal account.

After you login, there will be a prompt to add a site, type in your site information (URL) and it will return a id

## Modify your _config.yml

You want to drop down to the **Google Analytics** section and add the id obtained above, copy the id and it add it to your _config.yml 

```
google_analytics:
  id: # fill in your Google Analytics ID
```
## Wait!

It takes a few days, but if you entered in the **id** correctly, when you check back in a day or two you start to see data.

## It's Working!
I originally shared the site with a few coworkers and friends (Late October 2023) when the site was up, but then I posted it to LinkedIN (Early December 2023) to gain a better reach. 

I'm somewhat active on Social Media when the mood strikes, but it's mostly to highlight a big event or the kiddos - sending memes pretty standard stuff. Check out a this fresh screenshot as of (12/18/23) I'm not doing big numbers but it's still cool. For example, the page with the least views - in hindsight I might have reached more eyes if I had the title more specific to the tech I used (Palo Alto). After writing this I'll do just that and update the title for that post.

![screenshot of google analytics](/assets/images/google-analytics-1.png)