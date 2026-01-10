---
layout: page
title: Blog
tagline: Thoughts unfolded, one post at a time
description: Thoughts unfolded, one post at a time
---

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%B %-d, %Y" }}
    </li>
  {% endfor %}
</ul>
