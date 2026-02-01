---
layout: home
title: "Alex's Dev Journey"
permalink: /blog/
---

Welcome to my dev journey blog.

I write about backend development, Django, REST APIs, DevOps, and learning notes.

<div style="display: flex; gap: 2rem;">
  <div style="flex: 1;">
    <h2>All posts</h2>
    
    {% assign posts_by_month = site.posts | group_by_exp: "post", "post.date | date: '%Y-%m'" %}
    
    <ul>
      {% for month_group in posts_by_month %}
        {% assign month_date = month_group.name | append: '-01' | date: '%B %Y' %}
        <li id="{{ month_group.name }}" style="margin-bottom: 2rem;">
          <h3 style="color: #0969da; margin-bottom: 0.5rem;">{{ month_date }}</h3>
          <ul style="list-style: none; padding-left: 0;">
            {% for post in month_group.items %}
              <li style="margin-bottom: 0.5rem;">
                <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                <span style="color: #656d76;"> - {{ post.date | date: "%b %d, %Y" }}</span>
              </li>
            {% endfor %}
          </ul>
        </li>
      {% endfor %}
    </ul>
  </div>
  
  <div style="width: 200px; flex-shrink: 0;">
    <h2>Archive</h2>
    <ul style="list-style: none; padding-left: 0;">
      {% for month_group in posts_by_month %}
        {% assign month_date = month_group.name | append: '-01' | date: '%B %Y' %}
        <li style="margin-bottom: 0.5rem;">
          <a href="#{{ month_group.name }}">{{ month_date }}</a>
          <span style="color: #656d76;"> ({{ month_group.items | size }})</span>
        </li>
      {% endfor %}
    </ul>
  </div>
</div>
