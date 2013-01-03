---
layout: post
tags: jekyll
category: coding
summary: Adding tags to a Jekyll-powered blog.
---

**Notice:** Github doesn't support jekyll plugins.

## Using Tags

Add tags on frontmatter:

    tags: jekyll code

Create two files:

    _layouts/tag_index.html

and

    _plugins/_tag_gen.rb

In the tag_index file put:

    ---
    layout: default
    ---
    <h2 class="post_title">{{page.title}}</h2>
    <ul>
      {.% for post in site.posts %}
      {.% for tag in post.tags %}
      {.% if tag == page.tag %}
      <li class="archive_list">
        <time style="color:#666;font-size:11px;" datetime='{{post.date | date: "%Y-%m-%d"}}'>{{post.date | date: "%m/%d/%y"}}</time> <a class="archive_list_article_link" href='{{post.url}}'>{{post.title}}</a>
        <p class="summary">{{post.summary}}
        <ul class="tag_list">
          {% for tag in post.tags %}
          <li class="inline archive_list"><a class="tag_list_link" href="/tag/{{ tag }}">{{ tag }}</a></li>
          {% endfor %}
        </ul>
      </li>
      {.% endif %}
      {.% endfor %}
      {.% endfor %}
    </ul>

In the tag_gen file. put this:

    module Jekyll
      class TagIndex < Page
        def initialize(site, base, dir, tag)
          @site = site
          @base = base
          @dir = dir
          @name = 'index.html'
          self.process(@name)
          self.read_yaml(File.join(base, '_layouts'), 'tag_index.html')
          self.data['tag'] = tag
          tag_title_prefix = site.config['tag_title_prefix'] || 'Posts Tagged &ldquo;'
          tag_title_suffix = site.config['tag_title_suffix'] || '&rdquo;'
          self.data['title'] = "#{tag_title_prefix}#{tag}#{tag_title_suffix}"
        end
      end
      class TagGenerator < Generator
        safe true
        def generate(site)
          if site.layouts.key? 'tag_index'
            dir = site.config['tag_dir'] || 'tag'
            site.tags.keys.each do |tag|
              write_tag_index(site, File.join(dir, tag), tag)
            end
          end
        end
        def write_tag_index(site, dir, tag)
          index = TagIndex.new(site, site.source, dir, tag)
          index.render(site.layouts, site.site_payload)
          index.write(site.dest)
          site.pages << index
        end
      end
    end

## The magic happens

Jekyll needs a restart, if already running. After this, it creates new index files on _site/tags folder.

For github we need to commit this subdir.