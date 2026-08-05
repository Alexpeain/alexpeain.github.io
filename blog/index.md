---
layout: default
title: "Home"
---

<div class="hero-section">
  <!-- Avatar Illustration -->
  <div class="avatar-container">
    <img src="../images/my-notion-face-transparent.png" alt="Alex Peain - Backend Developer" class="avatar-img" />
  </div>

  <h1 class="hero-greeting">Hi, there!</h1>

  <p class="hero-bio-lead">
    I'm <strong>Alex Peain</strong>, and I build <strong>backend systems, APIs, and AI pipelines</strong>.
  </p>

  <p class="hero-bio-sub">
    Welcome to my personal site. Here I share notes on Python, Django, system architecture, DevOps, and my software development journey.
  </p>
</div>

<!-- Main Two-Column Grid -->
<div class="home-grid">
  
  <!-- Left Column: Quick Links Sidebar -->
  <aside class="quick-links-sidebar">
    <h3 class="section-title">QUICK LINKS</h3>
    <ul class="quick-links">
      <li>
        <a href="{{ '/about/' | relative_url }}">
          <span class="link-icon">👤</span> ABOUT ME
        </a>
      </li>
      <li>
        <a href="{{ '/projects/' | relative_url }}">
          <span class="link-icon">📁</span> ALL PROJECTS
        </a>
      </li>
      <li>
        <a href="{{ '/blog/' | relative_url }}">
          <span class="link-icon">📖</span> JOURNAL
        </a>
      </li>
      <li>
        <a href="{{ '/resume/' | relative_url }}">
          <span class="link-icon">📄</span> RESUME
        </a>
      </li>
      <li>
        <a href="{{ '/contact/' | relative_url }}">
          <span class="link-icon">✉️</span> CONTACT ME
        </a>
      </li>
    </ul>
  </aside>

  <!-- Right Column: Content Area -->
  <main class="featured-content">
    
    <!-- Section Header (Aligned Right like reference image) -->
    <div class="section-header-row">
      <h3 class="section-title text-right">LATEST POST</h3>
    </div>

    <!-- Featured Post Card -->
    {% assign latest_post = site.posts.first %}
    {% if latest_post %}
      <article class="featured-card">
        {% if latest_post.image %}
          <div class="featured-image-wrapper">
            <a href="{{ latest_post.url | relative_url }}">
              <img src="{{ latest_post.image | relative_url }}" alt="{{ latest_post.title }}" />
            </a>
          </div>
        {% endif %}

        <div class="featured-details">
          {% if latest_post.category %}
            <span class="category-badge">{{ latest_post.category | upcase }}</span>
          {% else %}
            <span class="category-badge">GENERAL</span>
          {% endif %}

          <h2 class="featured-title">
            <a href="{{ latest_post.url | relative_url }}">{{ latest_post.title }}</a>
          </h2>

          <p class="featured-excerpt">
            {{ latest_post.excerpt | strip_html | truncatewords: 25 }}
          </p>

          <a href="{{ latest_post.url | relative_url }}" class="read-more-link">READ MORE</a>
        </div>
      </article>
    {% endif %}

    <!-- All Posts Section -->
    <div class="all-posts-section">
      <h3 class="section-title">ALL POSTS</h3>
      <ul class="posts-list">
        {% for post in site.posts %}
          <li class="post-item">
            <a href="{{ post.url | relative_url }}" class="post-link">
              {{ post.title }}
            </a>
            <span class="post-date">
              {{ post.date | date: "%b %d, %Y" }}
            </span>
          </li>
        {% endfor %}
      </ul>
    </div>

  </main>
</div>