---
layout: post
title: create-documentation-site-using-github-pages-and-chirpy
date: 2023-10-25 12:00:00 -500
categories: [homelab,github,github-pages,chirpy]
tags: [github,github-pages,chirpy] # TAG names should always be lowercase, separated by commas
---

# Goals
- Have a public space to share my own crafted documentation.
- Use [markdown](https://commonmark.org/)

# Musings
- Since I've had a taste of [writing on github](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/quickstart-for-writing-on-github), I very quickly realized this is a great way for me to learn new things in areas I don't have much experience with i.e. GitHub.
- I like OneNote it's cool and serves it's purpose, Confluence is great and would prefer to just create content like this in there personally, but making a page public is only reserved for paying customers. Finally there's always the option to make a word document (or text file in notepad) and store it somewhere to never be referenced again.
- I'm certainly not a programmer/coder/developer (that I aspire to be anyway) but writing in markdown lets me play the role a little bit and gets the muscle memory going for using VSCode and a little CI/CD with GitHub (Pages).
- I didn't spend a ton of time researching, I actually started off creating repos with a journal and then linked content to the readme. I saw you could add a theme with [Jekyll](https://github.com/jekyll/jekyll)which led me down a rabbit hole to where I discovered a blog post by [Techno Tim](https://technotim.live/posts/jekyll-docs-site/). Honestly this post is really just a long winded way of sending you to his page.

# Prerequisites
- GitHub Account
- VSCode
- Operating System of choice (me: macOS)
- [Git Installed](https://git-scm.com/)

# Chirpy
Chirpy is phenomenal, it's the exact thing I wanted. The look and feel is super clean and functional (minimalist), easy to navigate, and fairly simple to implement.

## Getting Started
By completing the following steps you will have your own site running locally on your machine.

Review the [Getting Started Page](https://chirpy.cotes.page/posts/getting-started/) the bullets below are what helped me get started in the right direction after fumbling badly the first time.
- Install [Jekyll](https://jekyllrb.com/docs/installation/) I used the [macOS](https://jekyllrb.com/docs/installation/macos/) and followed them exactly, you'll want to ensure this is done correctly first.
- I used the [Chirpy Starter](https://github.com/cotes2020/chirpy-starter) option 1 by clicking on the link and selecting "use this template" from the installation section.
    * Must be Public
    * Name has to be <your_exact_username>.github.io
- Clone the Repository
```sh
# this command will clone the repo to the directory you're working in on your terminal
git clone git@github.com:<your_exact_username>/<your_exact_username>.github.io

# typing bundle will install dependencies
bundle

# typing code . will automatically open VScode from the terminal
code .

# serve the site on your local machine type "bundle exec jekyll s" in your terminal
bundle exec jekyll s
```
> Use your browser and go to the following URL http://localhost:4000/ and it will load your site locally

## Make It Your Own

Now that your site is running (locally) and you can see and it a click it, you can now make it your own.

- "_config.yml" file is where you want to start, it's all self explanatory and I pretty much filled in the fields I wanted to and stopped at the google analytics part and didn't go beyond. If vscode doesn't like a line 145 in your "_config.yml" it didn't like it in mine either and I just ignored it.
    * title:
    * description:
    * url - use: https://<your_exact_username>.github.io if you're not doing anything fancy
    * github / username:
    * twitter:
    * social:
    * avatar: if you have twitter you can copy the link of your profile pic and paste it here


> If you would like to view your updates you will need to do a ctrl + c in the terminal you ran "bundle exec jekyll s" on so that it stops serving the page and run the command again (essentially restarting it) I've found that if you make changes to the _config.yml you have to stop and start but adding posts you can just refresh the page (in the event it's not showing your updates you already know how to restart it)

The site should now have some personal touches you're ready to create posts!

## Jekyll Compose

I suppose it's just as easy to create files in the _posts folder with .md extensions but there's a plugin you can install called [Jekyll Compose](https://github.com/jekyll/jekyll-compose). This is a lot cleaner of a process and easy to use.

### Install the plugin 
```sh
# add this line to your "Gemfile"
gem 'jekyll-compose', group: [:jekyll_plugins]

# once it's saved you can run the bundle command from your terminal to install the plugin
bundle
```
My workflow has been pretty simple so far, start a draft...
```sh
bundle exec jekyll draft "draft-name.md"
```
> command creates a file in the _drafts directory with the name specified

When the draft is ready to publish
```sh
bundle exec jekyll publish "draft-name.md"
```
> file gets moved from _drafts to _posts directory and if all goes well you should be able to refresh your page http://localhost:4000/ and see your updated post.

## Push It Good
This is where the magic happens! If things are looking like you want it to and all files are saved you should have changes ready to commit (at the very least your _config.yml has been changed). I just use VSCode and don't really bother with running git commands.

- Ensure all the open files are saved
- Click on Source Control
- Stage all changes
- Enter in a comment, then click Commit
- Sync Changes - you will be prompted for your key

> Assuming everything went well you should be able to navigate to your actions tab on your github repo and see the "all the workflows" if those run and are successful you site is LIVE!

![Github Workflows](/assets/images/githubio-all-workflows.png)