---
layout: post
title: Jeykll Categories
date: 2018-04-24 15:48 +0100
categories: Tech
tags: 
  - Web
---

Moving from Octopress to a more modern version of Jeykll, getting categories up and working again has been a bit of a learning curve.


I want the urls to be human editable with something present at every level. I forego the usual url post structure for something simpler. In \_config.yml I define :

    permalink: /blog/:categories/:title:output_ext

The standard recommendation for Jeykll is to manually write the pages for your categories, I do not want to have to manage keeping those files in sync and adding or removing pages as Categories get updated. Therefor I am using the ['jekyll-categories'][1] gem.


In \_config.yml the category_dir variable needs to be set for this plugin.

    category_dir: "blog"

Gemfile

    group :jekyll_plugins do
      gem "jekyll-categories", "~> 0.0.2"
    end

then run

    > bundle

Create the post list for each category (\_layouts/category__index.html)
This will be used for pages matching  /blog/:categories
{% raw %}

    ---
    layout: page
    ---

    <ul>
    {% for post in site.categories[page.category] %}
    <li><a href="{{ post.url | absolute_url }}">
          {{ post.title }}
      </a></li>
    {% endfor %}
    </ul>
{% endraw %}




My top level categories page does not use the plugin. Create a Categories index, categories.html
This will be used for URLS matching  /blog

{% raw %}
    ---
    layout: default
    title: Categories
    permalink: /blog/
    ---
    <ul>
    {% for category in site.categories %}
    <li><a href="{{ site.url }}/blog/{{ category | first | downcase | url_encode }}/">{{ category | first }}</a> ({{ category[1].size }})</li>
    {% endfor %}
    </ul>
{% endraw %}

[1]: https://github.com/zroger/jekyll-categories
