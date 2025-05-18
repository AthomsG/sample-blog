---
layout: default
title: Home
---

# Welcome to My Tech Blog

This is where I share my thoughts, experiences, and tutorials about software development and technology.

## Recent Posts

<ul class="post-list">
  {% for post in site.posts limit:5 %}
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

<a href="{{ '/blog' | relative_url }}" class="all-posts">View All Posts</a>
