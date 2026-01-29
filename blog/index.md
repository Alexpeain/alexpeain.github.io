---
layout: home
title: "Alex's Dev Journey"
permalink: /blog/
---

Welcome to my dev journey blog.

I write about backend development, Django, REST APIs, DevOps, and learning notes.

## All posts

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span> – {{ post.date | date: "%b %d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
