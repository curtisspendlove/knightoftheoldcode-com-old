---
layout: post
title: A New Static Website
---

I'm a fairly persnickety kind of dude. I have very specific ways of doing things.

I generally work from my MacBook, but a linux or Windows system (with WSL, at least) should do.

I manage my servers and workstations with `Ansible`. But that's a fairly large sidebar. :)

The key portions for this article are `ruby`, which I manage with `asdf`, which in turn is managed with `homebrew`.

I like to start a new Jekyll site as follows:

```
$ mkdir knightoftheoldcode-com
$ cd knightoftheoldcode-com
$ gem install bundler jekyll
$ bundle exec jekyll new .
```

The above will generate a standard Jekyll template site. At the time I ran it for this site it provided the following directory structure.

```
├── 404.html
├── Gemfile
├── Gemfile.lock
├── _config.yml
├── _posts
│   └── 2020-08-03-welcome-to-jekyll.markdown
├── _site
│   ├── 2020
│   │   └── 08
│   │       └── 03
│   │           └── a-new-static-website.html
│   ├── 404.html
│   ├── about
│   │   └── index.html
│   ├── assets
│   │   ├── main.css
│   │   ├── main.css.map
│   │   └── minima-social-icons.svg
│   ├── feed.xml
│   ├── index.html
│   └── jekyll
│       └── update
│           └── 2020
│               └── 08
│                   └── 03
│                       └── welcome-to-jekyll.html
├── about.markdown
└── index.markdown
```

We will, of course, expand the site over time. We'll redesign it and add a lot of functionality. We'll take the journey together.

But for now, we'll just modify the basic portions of a new Jekyll site so we can get it up and deployed.

`_config.yml`:

```
# Welcome to Jekyll!
#
# This config file is meant for settings that affect your whole blog, values
# which you are expected to set up once and rarely edit after that. If you find
# yourself editing this file very often, consider using Jekyll's data files
# feature for the data you need to update frequently.
#
# For technical reasons, this file is *NOT* reloaded automatically when you use
# 'bundle exec jekyll serve'. If you change this file, please restart the server process.
#
# If you need help with YAML syntax, here are some quick references for you:
# https://learn-the-web.algonquindesign.ca/topics/markdown-yaml-cheat-sheet/#yaml
# https://learnxinyminutes.com/docs/yaml/
#
# Site settings
# These are used to personalize your new site. If you look in the HTML files,
# you will see them accessed via {{ site.title }}, {{ site.email }}, and so on.
# You can create any custom variable you would like, and they will be accessible
# in the templates via {{ site.myvariable }}.

title: Knight of the Old Code
email: curtis.spendlove@knightoftheoldcode.com
description: >- # this means to ignore newlines until "baseurl:"
  A puzzle? An enigma? Naw, just a redneck with a keyboard.
baseurl: "" # the subpath of your site, e.g. /blog
url: "https://knightoftheoldcode.com" # the base hostname & protocol for your site, e.g. http://example.com
twitter_username: curtisspendlove
github_username: curtisspendlove

# Build settings
theme: minima
show_drafts: true
plugins:
  - jekyll-feed
# Exclude from processing.
# The following items will not be processed, by default.
# Any item listed under the `exclude:` key here will be automatically added to
# the internal "default list".
#
# Excluded items can be processed by explicitly listing the directories or
# their entries' file path in the `include:` list.
#
# exclude:
#   - .sass-cache/
#   - .jekyll-cache/
#   - gemfiles/
#   - Gemfile
#   - Gemfile.lock
#   - node_modules/
#   - vendor/bundle/
#   - vendor/cache/
#   - vendor/gems/
#   - vendor/ruby/
```

At this point, I fire up Jekyll to serve a preview and take a look:

```
$ bundle exec jekyll serve

Configuration file: /Users/curtisspendlove/src/kotoc/knightoftheoldcode-com/_config.yml
            Source: /Users/curtisspendlove/src/kotoc/knightoftheoldcode-com
       Destination: /Users/curtisspendlove/src/kotoc/knightoftheoldcode-com/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
       Jekyll Feed: Generating feed for posts
                    done in 0.102 seconds.
 Auto-regeneration: enabled for '/Users/curtisspendlove/src/kotoc/knightoftheoldcode-com'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

As the instructions state, visiting `http://127.0.0.1:4000` will show my site preview.

The default is a new site with a single demonstration post.

I'll create a new post (I like the jekyll-compose gem for this, but we'll cover those sorts of things in the future).

For now, the sample post is sufficient.

We'll initialize a git repo locally and link it to a new repo created on GitHub.

```
$ git init
Initialized empty Git repository in /Users/curtisspendlove/src/kotoc/knightoftheoldcode-com/.git/

$ touch README.md
$ git add .
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   .gitignore
	new file:   .tool-versions
	new file:   404.html
	new file:   Gemfile
	new file:   Gemfile.lock
	new file:   README.md
	new file:   _config.yml
	new file:   _drafts/a-new-static-website.md
	new file:   about.markdown
	new file:   index.markdown

$ git commit -m "A New Jekyll Site"
[master (root-commit) 0610d96] A New Jekyll Site
 10 files changed, 365 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 .tool-versions
 create mode 100644 404.html
 create mode 100644 Gemfile
 create mode 100644 Gemfile.lock
 create mode 100644 README.md
 create mode 100644 _config.yml
 create mode 100644 _drafts/a-new-static-website.md
 create mode 100644 about.markdown
 create mode 100644 index.markdown

$ git remote add origin git@github.com:curtisspendlove/knightoftheoldcode-com.git
$ git push -u origin master
Enumerating objects: 13, done.
Counting objects: 100% (13/13), done.
Delta compression using up to 4 threads
Compressing objects: 100% (11/11), done.
Writing objects: 100% (13/13), 5.80 KiB | 1.93 MiB/s, done.
Total 13 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:curtisspendlove/knightoftheoldcode-com.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

```
