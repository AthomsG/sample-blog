---
layout: page
title: Blog
permalink: /blog/
---

# Blog Posts

Here you'll find all my blog posts, tutorials and thoughts.

<ul class="post-list">
  {% for post in site.posts %}
    <li>
      <h3>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h3>
      <span class="post-date">{{ post.date | date: "%B %d, %Y" }}</span>
      <p>{{ post.excerpt }}</p>
      <a href="{{ post.url | relative_url }}" class="read-more">Read More</a>
    </li>
  {% endfor %}
</ul>
