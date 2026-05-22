---
layout: page
title: Blog
tagline: Thoughts unfolded, one post at a time
description: Thoughts unfolded, one post at a time
---

{% for post in site.posts %}
  {% assign postYear = post.date | date: "%Y" %}
  {% if postYear != previousYear %}
    {% unless forloop.first %}
</ul>
<hr>
    {% endunless %}
<h2>{{ postYear }}</h2>
<ul>
    {% assign previousYear = postYear %}
  {% endif %}
<li>
<a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%B %-d, %Y" }}
</li>
  {% if forloop.last %}
</ul>
<hr>
  {% endif %}
{% endfor %}
