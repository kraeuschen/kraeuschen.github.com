---
layout: post
title: How to setup an twitter bootstrap with jekyll
category: coding
tags: jekyll github bootstrap
summary: How to setup an twitter bootstrap with jekyll
---

Twitter Bootstrap is a nice thing, but also the reason, why i couldn't use jekyll-bootstrap and did all the stuff recursivly on my own.

** Spoiler ** The javascript files of bootstrap leadings to a "page could not be rendered" error on github.
I guess the reason are comments in the js files, but i hasn't checked it.

## Download bootstrap

So go to the [bootstrap homepage](http://twitter.github.com/bootstrap/) and download the latest version.
You should unpack the file and copy all data into a dir called assets. Then remove all non-minifed js files and everything
works fine after pushing your commit.

## Change pathes on your layout

Now its time to change your layout file and add the bootstrap css/js files. Use the grid-system if you want for all pages.

    <link href="/assets/css/bootstrap.css" rel="stylesheet">
    <link href="/assets/css/docs.css" rel="stylesheet">
    <link href="/assets/css/bootstrap-responsive.css" rel="stylesheet">

    <div class="container">{{ content }}</div>

    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js" type="text/javascript"></script>
    <script src="/assets/js/bootstrap.min.js"></script>

Don't forget using the right jquery version.