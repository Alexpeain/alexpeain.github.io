---
layout: page
title: "Blog"
permalink: /blog/
---

<style>
  .blog-container {
    display: flex;
    gap: 3rem;
    max-width: 1200px;
    margin: 0 auto;
  }
  
  .sidebar {
    width: 220px;
    flex-shrink: 0;
  }
  
  .sidebar h3 {
    font-size: 1.1rem;
    margin-bottom: 1rem;
    color: #24292f;
  }
  
  .archive-list {
    list-style: none;
    padding: 0;
  }
  
  .archive-list li {
    margin-bottom: 0.75rem;
  }
  
  .archive-list a {
    text-decoration: none;
    color: #0969da;
    font-size: 0.95rem;
  }
  
  .archive-list a:hover {
    text-decoration: underline;
  }
  
  .post-count {
    color: #656d76;
    font-size: 0.85rem;
  }
  
  .main-content {
    flex: 1;
    min-width: 0;
  }
  
  .intro {
    margin-bottom: 2.5rem;
  }
  
  .intro p {
    color: #656d76;
    font-size: 1rem;
    line-height: 1.6;
  }
  
  .recent-posts {
    margin-bottom: 3rem;
  }
  
  .section-heading {
    font-size: 1.5rem;
    color: #24292f;
    margin-bottom: 1.25rem;
    padding-bottom: 0.5rem;
    border-bottom: 1px solid #d0d7de;
  }
  
  .posts-list {
    list-style: none;
    padding: 0;
  }
  
  .posts-list li {
    margin-bottom: 1rem;
  }
  
  .post-title {
    font-size: 1.1rem;
    font-weight: 500;
  }
  
  .post-title a {
    color: #0969da;
    text-decoration: none;
  }
  
  .post-title a:hover {
    text-decoration: underline;
  }
  
  .post-date {
    color: #656d76;
    font-size: 0.875rem;
    margin-left: 0.5rem;
  }
    
  /* Hide theme's auto-generated post-list */
  .post-list {
    display: none;
  }
</style>

<div class="blog-container">
  <aside class="sidebar">
    <h3>Archive</h3>
    {% assign posts_by_month = site.posts | group_by_exp: "post", "post.date | date: '%Y-%m'" %}
    <ul class="archive-list">
      {% for month_group in posts_by_month %}
        {% assign month_date = month_group.name | append: '-01' | date: '%B %Y' %}
        <li>
          <a href="#{{ month_group.name }}">{{ month_date }}</a>
          <span class="post-count">({{ month_group.items | size }})</span>
        </li>
      {% endfor %}
    </ul>
  </aside>
  
  <main class="main-content">
    <div class="intro">
      <p>Welcome to my dev journey blog. I write about backend development, Django, REST APIs, DevOps, and learning notes.</p>
    </div>
    
    <section class="recent-posts">
      <h2 class="section-heading">Recent posts</h2>
   
        
        {% for post in site.posts limit:5 %}
          <li>
            <div class="post-title">
              <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
              <span class="post-date">{{ post.date | date: "%b %d, %Y" }}</span>
            </div>
          </li>
        {% endfor %}
      </ul>
    </section>
  </main>
</div>
