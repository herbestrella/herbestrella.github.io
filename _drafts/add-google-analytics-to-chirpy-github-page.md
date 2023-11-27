---
layout: post
title: add-google-analytics-to-chirpy-github-page
date: 2023-11-22 12:00:00 -500
categories: [github,github-pages,chirpy]
tags: [github,github-pages,chirpy] # TAG names should always be lowercase, separated by commas
---

# Goal

Pretty simple and self explanatory, there's a section on the _config.yml that allows you to add google analytics. I've never used it before and I thought it would be neat to add some insight to the page.

## Google Analytics for Beginners

I found [Google Analytics Training](https://analytics.google.com/analytics/academy/course/6) after I got it implemented, that's how easy it is to setup.

## Setup Analytics

Browse to the [Sign-up](https://accounts.google.com/ServiceLogin?service=analytics), you'll need a google account to get started. I just used my personal account.

After you login there will be a prompt to add a site, type in your site information (URL) and it will return a id

## Modify your _config.yml

You want to drop down to the **Google Analytics** section and add an id, copy the id and it add it to your _config.yml 

```
google_analytics:
  id: # fill in your Google Analytics ID
```
## Wait

It takes a few days, but if you entered in the **id** correctly, when you check back in a day or two you start to see data.