---
layout: default
title: "Home"
---

<div class="hero-section">
  <!-- Avatar / Illustration -->
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

<div class="home-grid">
  <!-- Left Column: Quick Links -->
  <aside class="quick-links-sidebar">
    <h3 class="sidebar-title">QUICK LINKS</h3>
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

  <!-- Right Column: Featured Post & All Posts List -->
  <main class="featured-content">
    <!-- Featured / Latest Post -->
    <h3 class="featured-heading">LATEST POST</h3>

    {% assign latest_post = site.posts.first %}
    {% if latest_post %}
      <article class="featured-card">
        {% if latest_post.image %}
          <div class="featured-image">
            <a href="{{ latest_post.url | relative_url }}">
              <img src="{{ latest_post.image | relative_url }}" alt="{{ latest_post.title }}" />
            </a>
          </div>
        {% endif %}

        <div class="featured-details">
          {% if latest_post.category %}
            <span class="category-badge">{{ latest_post.category | upcase }}</span>
          {% endif %}

          <h2 class="featured-title">
            <a href="{{ latest_post.url | relative_url }}">{{ latest_post.title }}</a>
          </h2>

          <p class="featured-excerpt">
            {{ latest_post.excerpt | strip_html | truncatewords: 25 }}
          </p>

          <a href="{{ latest_post.url | relative_url }}" class="read-more-link">READ MORE →</a>
        </div>
      </article>
    {% endif %}

    <!-- All Blog Posts Section -->
    <div class="all-posts-section" style="margin-top: 2.5rem;">
      <h3 class="featured-heading">ALL POSTS</h3>
      <ul class="posts-list" style="list-style: none; padding: 0; margin: 0;">
        {% for post in site.posts %}
          <li style="margin-bottom: 0.75rem; display: flex; justify-content: space-between; align-items: center; border-bottom: 1px dashed var(--border-color, #e2e8f0); padding-bottom: 0.5rem;">
            <a href="{{ post.url | relative_url }}" style="font-weight: 600; text-decoration: none; color: var(--text-dark, #0f172a);">
              {{ post.title }}
            </a>
            <span style="font-size: 0.8rem; color: var(--text-light, #64748b);">
              {{ post.date | date: "%b %d, %Y" }}
            </span>
          </li>
        {% endfor %}
      </ul>
    </div>

  </main>
</div>
