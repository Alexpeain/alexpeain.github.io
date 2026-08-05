---
layout: default
title: "Home"
---
 ![Alex Peain - Backend Developer]({{ "/images/my-notion-face-transparent.png" | relative_url }}){: width="20%" }
<!-- Hero Section -->
<div class="hero-section" style="margin-bottom: 3.5rem; padding-bottom: 2rem; border-bottom: 1px solid #f0f0f0;">
  <div class="hero-text">
    <h1 class="hero-greeting" style="font-size: 2.2rem; font-weight: 800; margin-bottom: 1rem; color: #111;">Hi, there!</h1>
    <p class="hero-bio-lead" style="font-size: 1.1rem; line-height: 1.5; margin-bottom: 0.75rem; color: #222;">
      I'm <strong>Alex Peain</strong>, and I learn by building <strong>backend systems, APIs, and AI pipelines</strong>.
    </p>
    <p class="hero-bio-sub" style="font-size: 0.95rem; line-height: 1.6; color: #666; max-width: 750px; margin: 0;">
      This site is a journal of my journey—from documenting technical and software engineering challenges to personal development, learning notes, book reviews, and growth in life.
    </p>
  </div>
</div>

<!-- Main Two-Column Container -->
<div class="home-grid" style="display: flex; flex-direction: row; justify-content: space-between; align-items: flex-start; gap: 3rem; width: 100%;">
  
  <!-- Left Column: Quick Links Sidebar -->
  <aside class="quick-links-sidebar" style="width: 200px; min-width: 200px; flex-shrink: 0;">
    <h3 class="section-title" style="font-size: 0.8rem; font-weight: 700; letter-spacing: 0.08em; color: #999; text-transform: uppercase; margin-bottom: 1rem;">QUICK LINKS</h3>
    <ul class="quick-links" style="list-style: none; padding: 0; margin: 0;">
      <li style="margin-bottom: 0.65rem;">
        <a href="{{ '/about/' | relative_url }}" style="text-decoration: none; color: #555; font-size: 0.85rem; font-weight: 600;">
          <span class="link-icon">👤</span> ABOUT ME
        </a>
      </li>
      <li style="margin-bottom: 0.65rem;">
        <a href="{{ '/' | relative_url }}" style="text-decoration: none; color: #555; font-size: 0.85rem; font-weight: 600;">
          <span class="link-icon">📁</span> ALL PROJECTS
        </a>
      </li>
      <li style="margin-bottom: 0.65rem;">
        <a href="{{ '/blog/' | relative_url }}" style="text-decoration: none; color: #555; font-size: 0.85rem; font-weight: 600;">
          <span class="link-icon">📖</span> JOURNAL
        </a>
      </li>
      <li style="margin-bottom: 0.65rem;">
        <a href="{{ '/' | relative_url }}" style="text-decoration: none; color: #555; font-size: 0.85rem; font-weight: 600;">
          <span class="link-icon">📄</span> RESUME
        </a>
      </li>
      <li style="margin-bottom: 0.65rem;">
        <a href="{{ '/contact/' | relative_url }}" style="text-decoration: none; color: #555; font-size: 0.85rem; font-weight: 600;">
          <span class="link-icon">✉️</span> CONTACT ME
        </a>
      </li>
    </ul>
  </aside>

  <!-- Right Column: Recent Posts Content -->
  <main class="featured-content" style="flex: 1; min-width: 0;">
    <div class="section-header-row" style="margin-bottom: 1rem;">
      <h3 class="section-title" style="font-size: 0.8rem; font-weight: 700; letter-spacing: 0.08em; color: #999; text-transform: uppercase; text-align: right;">RECENT POSTS</h3>
    </div>

    <!-- Recent Posts Loop (Displays up to 3) -->
    {% for post in site.posts limit:3 %}
      <article class="featured-card" style="display: flex; gap: 1.25rem; align-items: flex-start; margin-bottom: 2rem;">
        
        {% if post.image %}
          <div class="featured-image-wrapper" style="width: 180px; min-width: 180px; flex-shrink: 0;">
            <a href="{{ post.url | relative_url }}">
              <img 
                src="{{ post.image | relative_url }}" 
                alt="{{ post.title }}" 
                style="width: 100%; height: 120px; object-fit: cover; border-radius: 4px; display: block;" 
              />
            </a>
          </div>
        {% endif %}

        <div class="featured-details" style="flex: 1;">
          <h2 class="featured-title" style="font-size: 1.1rem; font-weight: 800; margin: 0 0 0.5rem 0;">
            <a href="{{ post.url | relative_url }}" style="text-decoration: none; color: #111;">{{ post.title }}</a>
          </h2>

          <p class="featured-excerpt" style="font-size: 0.85rem; color: #555; margin-bottom: 0.5rem; line-height: 1.5;">
            {{ post.excerpt | strip_html | truncatewords: 20 }}
          </p>

          <a href="{{ post.url | relative_url }}" class="read-more-link" style="font-size: 0.75rem; font-weight: 700; color: #555; text-decoration: underline;">READ MORE</a>
        </div>

      </article>
    {% endfor %}

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

    
