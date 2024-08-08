---
layout: post
title: Jekyll Reference
author: Pablo E. Cortez
date: 2024-08-07 21:09 -0400
---

[Jekyll](https://jekyllrb.com) is a static site generator. A **static** site is 
a website where the content is the same for all users. It takes your content 
(static files like images, video, text, etc.) and runs it all through templates
written in HTML.

## Install Ruby and Jekyll

```sh
gem install jekyll bundler
```

## Create a new Jekyll site

You can either use the default starter project given to you by Jekyll or you 
can create one from scratch file by file.

```sh
jekyll new site-name
```

This creates a new folder called `site-name`, so navigate to it and to run your
project you start the local Jekyll server:

```sh
bundle exec jekyll serve
```

Visit your site by going to `http://localhost:4000`.

---

# Directory Structure

Your Jekyll project will have these necessary files and folders. 

`_config.yml`: Configuration settings for your entire site.

`_posts/`: This is where your posts go with the name format of 
`YYYY-MM-DD-your-title.md`.

`_layouts/`: Templates for your content (as HTML files).

`_includes/`: Reusable HTML components (like the navbar because we need it at 
the top of every page).

`_data/`: Data files (you can use YAML, JSON, CSV format)

`_site/`: Generated FINAL site. Do NOT edit or touch.

---

# Writing Content

## Creating a Post

Create a new markdown file `2024-08-07-my-title.md` and save it inside `_posts/`.

Include front matter at the top of your file:

```yaml
---
layout: post
title: My Title
author: Pablo E. Cortez
date: 2024-08-07 21:35 -0400
---
``` 

Then you start writing below the front matter using markdown, which Jekyll
will convert to HTML automatically. 

## Creating a Page

- Add a new Markdown or HTML file in the root directory.
- Include front matter if needed, for example:

```yaml
---
layout: page
title: About
permalink: /about
---

This is the about page in my website.
``` 

---

# Website Customization 

**Layouts**: Edit `_layouts/default.html` to change the main layout of your site.

You can create as many layout as you want.

**Includes**: Use `_includes/` for reusable components like headers, footers, navigation bars, etc.

Include them in your pages or posts by typing `{% include navigation.html %}`.

---

# Advanced Features

**Plugins**: Jekyll suports various plugins for Search Engine Optimization (SEO),
generating blog feedds, etc. To use a plugin, add it to your `Gemfile`.

This website uses the following plugins:

**Gemfile**

```ruby
source "https://rubygems.org"

gem "webrick"

group :jekyll_plugins do
  gem "github-pages"
  gem "jekyll-feed", "~> 0.12"
end
```

**_config.yml**

```yaml
plugins:
  - jekyll-feed
```

Just make sure to add your plugin to your `Gemfile` and also to your `_config.yml` file.

---

*On Friday, we will add the portion for deploying to Github Pages*.