---
layout: post
title: "Using Rake"
category: coding
tags: jekyll rake
summary: How to use rake for creating pages and posts
---

You can use rake for creating sites and posts. This file ist adopted from [jekyll-boostrap](http://jekyllbootstrap.com).

## Starting server

    rake preview

## Create page

    rake page name="about.md"

or

    rake page name="about/index.html"

## Create a post

    rake post title="A Title" [date="2012-02-09"]
