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
    color: #000000;    text-decoration: none;
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

    /* Mobile: Hide Archive sidebar for full-width main content */
    @media screen and (max-width: 768px) {
          .sidebar {
                  display: none;
                }
    
    
      /* Pagination Styles */
      .pagination {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 1rem;
            margin-top: 2rem;
          }

        .pagination-btn {
              padding: 0.5rem 1rem;
              background: #24292f;
              color: white;
              border: none;
              border-radius: 4px;
              cursor: pointer;
              font-size: 0.9rem;
            }

        .pagination-btn:hover {
              background: #0969da;
            }

        .pagination-btn:disabled {
              background: #d0d7de;
              cursor: not-allowed;
            }

        .page-info {
              color: #656d76;
              font-size: 0.9rem;
            }
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
            <ul class="posts-list">
    {% for post in site.posts %}
          <li data-month="{{ post.date | date: '%Y-%m' }}">
            <div class="post-title">
                        <a href="{{ post.url }}">{{ post.title }}</a>
                  <span class="post-date">{{ post.date | date: "%b %d, %Y" }}</span>
            </div>
          </li>
        {% endfor %}
      </ul>

          <!-- Pagination Controls -->
              <div class="pagination">
                    <button id="prev-page" class="pagination-btn">← Previous</button>
                          <span id="page-info" class="page-info">Page 1</span>
                                <button id="next-page" class="pagination-btn">Next →</button>
                                    </div>
    </section>
  </main>
  </div>
      

<script>
// Filter posts by month when archive link is clicked
function filterPosts() {
  const hash = window.location.hash.substring(1); // Remove # from hash
  const posts = document.querySelectorAll('.recent-posts li[data-month]');
  
  posts.forEach(post => {
    if (!hash || post.getAttribute('data-month') === hash) {
      post.style.display = '';
    } else {
      post.style.display = 'none';
    }
  });
}

// Run on page load
filterPosts();

  // Pagination functionality
  const postsPerPage = 5;
  let currentPage = 1;
  const allPosts = Array.from(document.querySelectorAll('.posts-list li'));
  const totalPages = Math.ceil(allPosts.length / postsPerPage);

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

  // Initialize pagination
  showPage(currentPage);

// Run when hash changes
window.addEventListener('hashchange', filterPosts);
</script>
