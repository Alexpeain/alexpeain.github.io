---
layout: default
title: "Home"
---

<div class="hero-section">
  <!-- Avatar / Illustration -->
  <div class="avatar-container">
    <img src="/assets/images/avatar.png" alt="Avatar Illustration" class="avatar-img" />
  </div>

  <h1 class="hero-greeting">Hi, there!</h1>

  <p class="hero-bio-lead">
    I'm <strong>Alex</strong>, and I build <strong>backend systems, APIs, and AI pipelines</strong>.
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
        <a href="/about/">
          <span class="link-icon">👤</span> ABOUT ME
        </a>
      </li>
      <li>
        <a href="/projects/">
          <span class="link-icon">📁</span> ALL PROJECTS
        </a>
      </li>
      <li>
        <a href="/blog/">
          <span class="link-icon">📖</span> JOURNAL
        </a>
      </li>
      <li>
        <a href="/resume/">
          <span class="link-icon">📄</span> RESUME
        </a>
      </li>
      <li>
        <a href="/contact/">
          <span class="link-icon">✉️</span> CONTACT ME
        </a>
      </li>
    </ul>
  </aside>

  <!-- Right Column: Featured / Latest Posts -->
  <main class="featured-content">
    <h3 class="featured-heading">LATEST POST</h3>

    {% assign latest_post = site.posts.first %}
    {% if latest_post %}
      <article class="featured-card">
        {% if latest_post.image %}
          <div class="featured-image">
            <a href="{{ latest_post.url | relative_url }}">
              <img src="{{ latest_post.image }}" alt="{{ latest_post.title }}" />
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
            {{ latest_post.excerpt | strip_html | truncatewords: 30 }}
          </p>

          <a href="{{ latest_post.url | relative_url }}" class="read-more-link">READ MORE →</a>
        </div>
      </article>
    {% endif %}

  </main>
</div>
