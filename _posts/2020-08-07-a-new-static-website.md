---
layout: post
title: A New Static Website
date: 2020-08-07 18:06 -0600
---
I'm a fairly persnickety kind of dude. I have very specific ways of doing things.

I generally work from my MacBook, but a linux or Windows system (with WSL, at least) should do.

I manage my servers and workstations with `Ansible`. But that's a fairly large sidebar. :)

The key portions for this article are `ruby`, which I manage with `asdf`, which in turn is managed with `homebrew`.

## Generate a New Static Site with Jekyll

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

## From Your Computer, to Theirs

Finally, we'll push `master` to Heroku. Heroku is an awesome little service (ok, they are a vastly huge service) that help you scale from initial concept to full-blown highly-available production apps.

We, however, will also investigate how to build out your own virtual servers to host your site. You can use anything you want, such as AWS, Google, Azure, etc; but I prefer Linode.

This site, after all, is about learning how to do it the "best practices" way.

But it _never_ hurts to start with the _easy_ way.

```
$ heroku create knightoftheoldcode-com
Creating ⬢ knightoftheoldcode-com... done
https://knightoftheoldcode-com.herokuapp.com/ | https://git.heroku.com/knightoftheoldcode-com.git

```

Heroku requires a definition of how your app should run:

`Procfile`:

```
web: jekyll serve -P $PORT --no-watch --host 0.0.0.0
```

The `heroku create ...` command should have added a `git remote` endpoint. We can use this to easily deploy changes to Heroku (magic, I daresay).

```
$ git remote -v
heroku	https://git.heroku.com/knightoftheoldcode-com.git (fetch)
heroku	https://git.heroku.com/knightoftheoldcode-com.git (push)
origin	git@github.com:curtisspendlove/knightoftheoldcode-com.git (fetch)
origin	git@github.com:curtisspendlove/knightoftheoldcode-com.git (push)
```

We can publish via `git push heroku`:

````
$ git push heroku
Enumerating objects: 22, done.
Counting objects: 100% (22/22), done.
Delta compression using up to 4 threads
Compressing objects: 100% (20/20), done.
Writing objects: 100% (22/22), 7.31 KiB | 3.66 MiB/s, done.
Total 22 (delta 5), reused 0 (delta 0), pack-reused 0
remote: Compressing source files... done.
remote: Building source:
remote:
remote: -----> Ruby app detected
remote: -----> Installing bundler 2.0.2
remote: -----> Removing BUNDLED WITH version in the Gemfile.lock
remote: -----> Compiling Ruby
remote: -----> Using Ruby version: ruby-2.6.6
remote: -----> Installing dependencies using bundler 2.0.2
remote:        Running: bundle install --without development:test --path vendor/bundle --binstubs vendor/bundle/bin -j4 --deployment
remote:        The dependency tzinfo (~> 1.2) will be unused by any of the platforms Bundler is installing for. Bundler is installing for ruby but the dependency is only for x86-mingw32, x64-mingw32, x86-mswin32, java. To add those platforms to the bundle, run `bundle lock --add-platform x86-mingw32 x64-mingw32 x86-mswin32 java`.
remote:        The dependency tzinfo-data (>= 0) will be unused by any of the platforms Bundler is installing for. Bundler is installing for ruby but the dependency is only for x86-mingw32, x64-mingw32, x86-mswin32, java. To add those platforms to the bundle, run `bundle lock --add-platform x86-mingw32 x64-mingw32 x86-mswin32 java`.
remote:        The dependency wdm (~> 0.1.1) will be unused by any of the platforms Bundler is installing for. Bundler is installing for ruby but the dependency is only for x86-mingw32, x64-mingw32, x86-mswin32. To add those platforms to the bundle, run `bundle lock --add-platform x86-mingw32 x64-mingw32 x86-mswin32`.
remote:        Fetching gem metadata from https://rubygems.org/.........
remote:        Fetching public_suffix 4.0.5
remote:        Using bundler 2.0.2
remote:        Fetching colorator 1.1.0
remote:        Fetching concurrent-ruby 1.1.6
remote:        Installing colorator 1.1.0
remote:        Installing concurrent-ruby 1.1.6
remote:        Installing public_suffix 4.0.5
remote:        Fetching eventmachine 1.2.7
remote:        Installing eventmachine 1.2.7 with native extensions
remote:        Fetching http_parser.rb 0.6.0
remote:        Installing http_parser.rb 0.6.0 with native extensions
remote:        Fetching ffi 1.13.1
remote:        Installing ffi 1.13.1 with native extensions
remote:        Fetching forwardable-extended 2.6.0
remote:        Installing forwardable-extended 2.6.0
remote:        Fetching rb-fsevent 0.10.4
remote:        Installing rb-fsevent 0.10.4
remote:        Fetching rexml 3.2.4
remote:        Installing rexml 3.2.4
remote:        Fetching liquid 4.0.3
remote:        Installing liquid 4.0.3
remote:        Fetching mercenary 0.4.0
remote:        Installing mercenary 0.4.0
remote:        Fetching rouge 3.21.0
remote:        Installing rouge 3.21.0
remote:        Fetching safe_yaml 1.0.5
remote:        Installing safe_yaml 1.0.5
remote:        Fetching unicode-display_width 1.7.0
remote:        Installing unicode-display_width 1.7.0
remote:        Fetching addressable 2.7.0
remote:        Installing addressable 2.7.0
remote:        Fetching i18n 1.8.5
remote:        Installing i18n 1.8.5
remote:        Fetching pathutil 0.16.2
remote:        Installing pathutil 0.16.2
remote:        Fetching kramdown 2.3.0
remote:        Installing kramdown 2.3.0
remote:        Fetching terminal-table 1.8.0
remote:        Installing terminal-table 1.8.0
remote:        Fetching kramdown-parser-gfm 1.1.0
remote:        Installing kramdown-parser-gfm 1.1.0
remote:        Fetching sassc 2.4.0
remote:        Fetching rb-inotify 0.10.1
remote:        Installing rb-inotify 0.10.1
remote:        Installing sassc 2.4.0 with native extensions
remote:        Fetching listen 3.2.1
remote:        Installing listen 3.2.1
remote:        Fetching jekyll-watch 2.2.1
remote:        Installing jekyll-watch 2.2.1
remote:        Fetching em-websocket 0.5.1
remote:        Installing em-websocket 0.5.1
remote:        Fetching jekyll-sass-converter 2.1.0
remote:        Installing jekyll-sass-converter 2.1.0
remote:        Fetching jekyll 4.1.1
remote:        Installing jekyll 4.1.1
remote:        Fetching jekyll-compose 0.12.0
remote:        Fetching jekyll-seo-tag 2.6.1
remote:        Fetching jekyll-feed 0.15.0
remote:        Installing jekyll-compose 0.12.0
remote:        Installing jekyll-seo-tag 2.6.1
remote:        Installing jekyll-feed 0.15.0
remote:        Fetching minima 2.5.1
remote:        Installing minima 2.5.1
remote:        Bundle complete! 7 Gemfile dependencies, 32 gems now installed.
remote:        Gems in the groups development and test were not installed.
remote:        Bundled gems are installed into `./vendor/bundle`
remote:        Post-install message from i18n:
remote:
remote:        HEADS UP! i18n 1.1 changed fallbacks to exclude default locale.
remote:        But that may break your application.
remote:
remote:        If you are upgrading your Rails application from an older version of Rails:
remote:
remote:        Please check your Rails app for 'config.i18n.fallbacks = true'.
remote:        If you're using I18n (>= 1.1.0) and Rails (< 5.2.2), this should be
remote:        'config.i18n.fallbacks = [I18n.default_locale]'.
remote:        If not, fallbacks will be broken in your app by I18n 1.1.x.
remote:
remote:        If you are starting a NEW Rails application, you can ignore this notice.
remote:
remote:        For more info see:
remote:        https://github.com/svenfuchs/i18n/releases/tag/v1.1.0
remote:
remote:        Bundle completed (197.60s)
remote:        Cleaning up the bundler cache.
remote: -----> Detecting rake tasks
remote:
remote: ###### WARNING:
remote:
remote:        You have not declared a Ruby version in your Gemfile.
remote:
remote:        To declare a Ruby version add this line to your Gemfile:
remote:
remote:        ```
remote:        ruby "2.6.6"
remote:        ```
remote:
remote:        For more information see:
remote:          https://devcenter.heroku.com/articles/ruby-versions
remote:
remote:
remote: -----> Discovering process types
remote:        Procfile declares types     -> web
remote:        Default types for buildpack -> console, rake
remote:
remote: -----> Compressing...
remote:        Done: 38.2M
remote: -----> Launching...
remote:        Released v4
remote:        https://knightoftheoldcode-com.herokuapp.com/ deployed to Heroku
remote:
remote: Verifying deploy... done.
To https://git.heroku.com/knightoftheoldcode-com.git
 * [new branch]      master -> master
````

Phwew! We get a _lot_ of output from Heroku...but that's good. This helps you know if it was a successful deploy, or what went wrong if not.

Our pretty simple application here shouldn't have any deployment issues. But if you do, try your Google-fu on for size; I bet you can pretty easily fix it. If not, feel free to drop me a line and I'll try to help.

Let's check it out!

```
$ heroku open
```

Heroku's CLI utility should launch your browser and open a new tab pointing to your site:

https://[HEROKU_APP_NAME].herokuapp.com/

There's a lot more we can do with Heroku, including custom domains, etc. We'll cover some of that in a future article.

The nifty part, for now, if you want to publish any updates, simply make your updates and push them to GitHub and also Heroku:

```
$ git add .
$ git commit -m "Add Finishing Touches to 'A New Static Website' Article"
$ git push origin
$ git push heroku
```

For now, you have a website publicly available to which you can refer people. Imagine how happy you'll be when you get it to a point you're comfortable adding to your resume.
