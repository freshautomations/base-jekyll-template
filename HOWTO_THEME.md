# How to use this template as a Jekyll theme

## Overview
The template was updated with a few things to be more in line with Jekyll theme expectations. Most of what is on the
[Jekyll themes](https://jekyllrb.com/docs/themes/) page apply, except that this is not a Gem-based theme. We work around
that using the `jekyll-remote-theme` Gem.

## Setup
The quickest way to set up a website using this theme is to use the following `Gemfile`.

Filename Gemfile:
```
source "https://rubygems.org"

gem "jekyll", "~> 3.8"
gem "jekyll-remote-theme", "~> 0.4.2"
gem "jekyll-seo-tag"
gem "jekyll-feed"
gem "jekyll-sitemap"
gem "jekyll-archives"
```

Then run:
```shell script
bundle install
```

You see that we installed the `jekyll-remote-theme` Gem. Instead of a local theme, we are going to use the `remote_theme`
parameter in our `_config.yml` to invoke this theme.

Filename _config.yml:
```yaml
title: My Tutorials
remote_theme: "freshautomations/base-jekyll-template"

plugins:
  - jekyll-remote-theme
  - jekyll-sitemap
  - jekyll-seo-tag
  - jekyll-feed
  - jekyll-archives

defaults:
  -
    scope:
      path: "index.html"
    values:
      body_class: "show_hero_search"
      hero_search_title: "My Tutorials Search"
      hero_search_tagline: "Knock yourself out."
```

We are almost done. The theme is ready to be used, we just need some webpages to make use of it. You can see that we overrode
the search box title and tagline - if the search box is in `index.html` so make sure that there is an `index.html`.

We are going to use the default settings without any changes:

Filename index.html:
```yaml
---
layout: home
---
```

And since we have a search box on the main page that points to a results page called `search.html`, we should create
that results page too. (Also using defaults.)

Filename search.html:
```yaml
---
layout: search
---
```

That's it. The site can be started using
```shell script
bundle exec jekyll serve
```

And it will present the site with the Base theme and an operating search box. Now `_posts` and other features of the site
can be added using the usual Jekyll mechanisms and the documentation of the theme.

## Adding an FAQ
The FAQ was also made into a layout for easier handling. You can add an HTML like this:

Filename faq.html:
```yaml
---
layout: faq
---
```

Then add questions and answers into the `_data/faq.yml` file, like this:

Filename _data/faq.yml:
```yaml
- question: Who am I?
  answer: You're a robot.
- question: What's my purpose?
  answer: You pass butter.
```

## Adding custom JavaScript code
Custom Javascript code can be added by adding a file `assets/js/scripts.js`. The script will be automatically imported and 
executed at the end of the header, after jQuery was imported. (So you can use jQuery in it.)

## Adding custom CSS
Custom CSS code can be added by adding file `_sass/custom-styles.scss`. You can add additional files into `assets/css` as
long as you import them in the `custom-styles.scss` file.

## An example site
The site [Rust Example](https://rust-examples.com) was built using this theme. You can find its source code on
[GitHub](https://github.com/rust-examples/rust-examples.com). It also has a good example on how to import additional
external JavaScript code with custom CSS.