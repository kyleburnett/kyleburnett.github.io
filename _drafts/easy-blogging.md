---
layout: post
title:  "GitHub Pages + Jekyll"
date:   2015-11-17 16:16:01 -0600
---

My goal at the start of 2018 was to blog more consistently. My old blog setup consisted of a WordPress site hosted by DigitalOcean. This amounted to $5 per month for the server plus $1 per month for backups, which isn't bad at all. DigitalOcean has a great user interface, and they really try to make system administration as easy as possible.

The problem was that I wasn't blogging to learn about system administration. I wanted a platform to express my thoughts and build my web presence. DigitalOcean + Wordpress, as easy as it was to set up, left a lot that had to be maintained. I was confronted with things like keeping Wordpress up to date, the database online, and the site secure.

Even for someone like me (who develops web applications all day), this was too much to manage and too much of a distraction from actually writing posts. Several times I would go to the site with the intention of writing something and find that it was unresponsive or that the MySQL server was offline for some reason. I would spend an hour or so finding my password, signing in to the server, and fixing the problem, which would leave me unmotivated to actually write anything.

So I went looking for an alternative. My criteria for a blogging solution was simple.

1. Inexpensive.
2. Easy to Publish Content.
3. Little to No Maintenance.
4. Easy to Customize.

I eventually came to GitHub pages. I'm not entirely sure how I found it. It might have been a NodeJS library that was hosting their documentation on the site. Their introduction video on [https://pages.github.com/](https://pages.github.com/) really caught my eye. Especially the part where they talk about the excessiveness of the various blogging options out there. I was also drawn to the simplicity of [Jekyll](https://jekyllrb.com/), the static site generator. The listed [example sites](https://github.com/jekyll/jekyll/wiki/Sites) seemed wonderfully simple.

I want to spend a little time now explaining how I got set up and how my blog site works.

# Initial Repository Setup

First, I created a repository using the [user pages setup](https://help.github.com/articles/user-organization-and-project-pages/#user--organization-pages) (be sure to follow the repository naming rules) and then went looking for some themes on which to base my site. I really liked the simplicity of [Tale](https://chesterhow.github.io/tale/), so I based my site heavily on that. I copied files from the demo and started to get my environment set up. I'll break that down next.

# Environment Setup

## Step 1: Download Prerequisites

Jekyll requires Ruby and Ruby Gems. Mac comes with a ruby version but the operating system will prevent some gems from being installed for that version. To get around this, use `rbenv` to install independent versions of Ruby.

1. Install using homebrew.
   ```
   $ brew install rbenv
   ```
2. Run `rbenv init` and follow the instructions to set up `rbenv` integration with your shell.
3. Close and reopen the terminal window.
4. Run the following script to check that `rbenv` was installed correctly.
   ```
   $ curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
   ```

## Step 2: Install Ruby Version

Navigate to the project directory, install the most recent, stable version of Ruby.

```
$ rbenv local 2.5.0
```

A file called `.ruby-version` will be added to the current directory. Add this to the project's `.gitignore` file.

## Step 3: Install `bundler`

```
$ gem install bundler
```

## Step 4: Install Jekyll Using `bundler`

Create a Gemfile in the project directory with the following contents

```
source 'https://rubygems.org'
gem 'github-pages', group: :jekyll_plugins
```

```
$ bundle install
```

## Step 5: Server Jekyll Site

Run the following command.

```
$ bundle exec jekyll serve
```

# Deployment

This was the best part. Once I'd made some customizations to the theme, all I had to do was commit and push to master as usual.

```
git add --all && git commit -m "Initial site skeleton" && git push origin master
```

Overall I'm very pleased with how it all turned out, and I'm looking forward to writing some posts.
