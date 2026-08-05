---
layout: default
title: "Blog"
permalink: /blog/
---

<div class="blog-container">
  <!-- Sidebar: Archive Section -->
  <aside class="sidebar">
    <div class="sidebar-box">
      <h3>Archive</h3>
      {% assign posts_by_month = site.posts | group_by_exp: "post", "post.date | date: '%Y-%m'" %}
      <ul class="archive-list">
        {% for month_group in posts_by_month %}
          {% assign month_date = month_group.name | append: '-01' | date: '%B %Y' %}
          <li>
            <a href="#{{ month_group.name }}">
              <span>{{ month_date }}</span>
              <span class="post-count">{{ month_group.items | size }}</span>
            </a>
          </li>
        {% endfor %}
      </ul>
    </div>
  </aside>

  <!-- Main Content: Intro & Post List -->
  <main class="main-content">
    <div class="intro">
      <p>Welcome to my dev journey blog. I write about backend development, Django, REST APIs, DevOps, and learning notes.</p>
    </div>

    <section class="recent-posts">
      <h2 class="section-heading">Recent Posts</h2>
      <ul class="posts-list">
        {% for post in site.posts %}
          <li data-month="{{ post.date | date: '%Y-%m' }}">
            <a href="{{ post.url | relative_url }}" class="post-card">
              <div class="post-info">
                <h3 class="post-title">{{ post.title }}</h3>
                <span class="post-date">{{ post.date | date: "%b %d, %Y" }}</span>
              </div>
            </a>
          </li>
        {% endfor %}
      </ul>

      <!-- Pagination -->
      <div class="pagination">
        <button id="prev-page" class="pagination-btn">← Previous</button>
        <span id="page-info" class="page-info">Page 1</span>
        <button id="next-page" class="pagination-btn">Next →</button>
      </div>
    </section>

  </main>
</div>

<script>
  const postsPerPage = 5;
  let currentPage = 1;
  const allPosts = Array.from(document.querySelectorAll('.posts-list li'));
  const totalPages = Math.ceil(allPosts.length / postsPerPage) || 1;

  function showPage(page) {
    const start = (page - 1) * postsPerPage;
    const end = start + postsPerPage;

    allPosts.forEach((post, index) => {
      post.style.display = (index >= start && index < end) ? '' : 'none';
    });

    document.getElementById('page-info').textContent = `Page ${page} of ${totalPages}`;
    document.getElementById('prev-page').disabled = (page === 1);
    document.getElementById('next-page').disabled = (page === totalPages);
  }

  document.getElementById('prev-page').addEventListener('click', () => {
    if (currentPage > 1) {
      currentPage--;
      showPage(currentPage);
    }
  });

  document.getElementById('next-page').addEventListener('click', () => {
    if (currentPage < totalPages) {
      currentPage++;
      showPage(currentPage);
    }
  });

  showPage(currentPage);
</script>
