---
layout: post
title:  "GitHub Pages + Jekyll"
date:   2018-03-17 14:20:00 -0400
---

My goal at the start of 2018 was to blog more consistently. My old blog setup consisted of a WordPress site hosted by DigitalOcean. This amounted to $5 per month for the server plus $1 per month for backups, which isn't bad at all. DigitalOcean has a great user interface, and they really try to make system administration as easy as possible.

The problem was that I wasn't blogging to learn about system administration. I wanted a platform to express my thoughts and build my web presence. DigitalOcean + Wordpress, as easy as it was to set up, left a lot that had to be maintained. I was confronted with things like keeping Wordpress up to date, the database online, and the site secure.

Even for someone like me (who develops web applications all day), this was too much to manage and too much of a distraction from actually writing posts. Several times I would go to the site with the intention of writing something and find that it was unresponsive or that the MySQL server was offline for some reason. I would spend an hour or so finding my password, signing in to the server, and fixing the problem, which would leave me unmotivated to actually write anything.

So I went looking for an alternative. My criteria for a blogging solution was simple.

1. Inexpensive.
2. Easy to Publish Content.
3. Little to No Maintenance.
4. Easy to Customize.

I eventually came to GitHub pages. I'm not entirely sure how I found it. It might have been a NodeJS library that was hosting their documentation on the site. I really identified with their introduction video at [https://pages.github.com/](https://pages.github.com/) especially the part where they talk about the excessiveness of the various blogging options out there. I was also drawn to the simplicity of [Jekyll](https://jekyllrb.com/), the static site generator. The listed [example sites](https://github.com/jekyll/jekyll/wiki/Sites) seemed wonderfully simple, which is exactly what I was looking for.

I want to spend a little time now explaining how I got set up and how my blog site works. Note that at least some of these instructions will be specific to the Mac or other Linux based environments.

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

I won't go into detail about how to set up the Jekyll project itself. This is covered well in the [Jekyll documentation](https://jekyllrb.com/docs/home/) and the particulars can depend on the theme you use. I do want to talk about how I go from a draft to a published article because the simplicity of this process is what drew me to GitHub Pages + Jekyll in the first place.

Drafts are important because they allow you to save progress on a post you're writing (by committing to source control) without affecting the content you're ready to publish. Drafts are stored in the `_drafts` directory, and you can serve your site with drafts mode turned on by using the `--drafts` switch.

```
$ bundle exec jekyll serve --drafts
```

When you're ready to publish the post, you'll want to move the draft into the `_posts` directory and name the file according to the rules laid out in the [Jekyll's "Writing posts" guide](https://jekyllrb.com/docs/posts/). I also like to set the date in the site's [front matter](https://jekyllrb.com/docs/frontmatter/). Once your changes have been committed or merged into the master branch on GitHub, your blog site will be updated with your new post!
