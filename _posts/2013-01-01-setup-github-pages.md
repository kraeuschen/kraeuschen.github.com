---
layout: post
title: How to setup an github based blog
category: coding
tags: jekyll github
summary: How to setup an github based blog
---

## Create repo

Go to the Github Dashboard and create a new repository named USERNAME.github.com
It has to be exactly the same name as your username.

You can use the [automatic page generator](https://help.github.com/articles/creating-pages-with-the-automatic-generator) with templates
or setup an [page manually](https://help.github.com/articles/creating-project-pages-manually).

I used the page generator for the beginnin and removed all content except the index.html

## Setup jekyll structure

Follow the instructions on the [github manual](https://help.github.com/articles/using-jekyll-with-pages).

You will need to install some gems on your machine and setup a [directory structure](https://github.com/mojombo/jekyll/wiki/usage)

Change the _config.yml and set some [config vars](https://github.com/mojombo/jekyll/wiki/Configuration):

    auto: true
    pygments: true
    exclude: [".rvmrc", ".rbenv-version", "README.md", "Rakefile", "changelog.md"]
    markdown: rdiscount
    permalink: /:year/:month/:day/:title
    rdiscount extensions: [smart]

If you run

    jekyll --server

it spawns an webserver on http://0.0.0.0:4000/.

## Using markdown

Set your markdown engine in your _config.yml.

Jekyll will parse .md files and creates html. You can add posts in the _posts directory,
with your permalink-scheme.

e.g create and file on posts/2013-01-01-setup-github-pages.md with content.

    This is a test post writen in markdown. To learn more about markdown check
    out the [documentation](http://daringfireball.net/projects/markdown/).

See the result on http://0.0.0.0:4000/2013/01/01/setup-github-pages/

This is a test post writen in markdown. To learn more about markdown check
out the [documentation](http://daringfireball.net/projects/markdown/).
