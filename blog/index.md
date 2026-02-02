---
layout: page
title: "Blog"
permalink: /blog/
---

<style>
    /* CSS Variables for Theme Colors */
    :root {
          --bg-primary: #ffffff;
          --bg-secondary: #f6f8fa;
          --text-primary: #24292f;
          --text-secondary: #656d76;
          --text-link: #000000;
          --border-color: #d0d7de;
          --card-bg: #ffffff;
          --card-shadow: rgba(0, 0, 0, 0.05);
          --btn-bg: #24292f;
          --btn-text: #ffffff;
          --btn-hover: #0969da;
        }

    /* Dark Theme */
    [data-theme="dark"] {
          --bg-primary: #0d1117;
          --bg-secondary: #161b22;
          --text-primary: #e6edf3;
          --text-secondary: #8b949e;
          --text-link: #e6edf3;
          --border-color: #30363d;
          --card-bg: #161b22;
          --card-shadow: rgba(0, 0, 0, 0.3);
          --btn-bg: #21262d;
          --btn-text: #c9d1d9;
          --btn-hover: #388bfd;
        }

    /* Apply theme colors */
    body {
          background-color: var(--bg-primary);
          color: var(--text-primary);
          transition: background-color 0.3s ease, color 0.3s ease;
        }

    /* Theme Toggle Button */
    .theme-toggle {
          position: fixed;
          top: 20px;
          right: 20px;
          background: var(--btn-bg);
          border: 2px solid var(--border-color);
          border-radius: 50%;
          width: 50px;
          height: 50px;
          cursor: pointer;
          display: flex;
          align-items: center;
          justify-content: center;
          font-size: 1.5rem;
          transition: all 0.3s ease;
          z-index: 1000;
          box-shadow: 0 2px 8px var(--card-shadow);
        }

    .theme-toggle:hover {
          transform: scale(1.1);
          background: var(--btn-hover);
        }

    /* Update existing elements with theme variables */
    .intro p,
    .post-date,
    .post-count {
          color: var(--text-secondary) !important;
        }

    .post-title a,
    .archive-list a {
      color: var(--text-link) !important;
        }

    .section-heading,
    .sidebar h3,
    h2, h3 {
          color: var(--text-primary) !important;
        }

    .section-heading {
          border-bottom-color: var(--border-color) !important;
        }

    .pagination-btn {
          background: var(--btn-bg) !important;
          color: var(--btn-text) !important;
        }

    .pagination-btn:hover {
          background: var(--btn-hover) !important;
        }

    .page-info {
          color: var(--text-secondary) !important;
        }
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

    <!-- Theme Toggle Button -->
    <button class="theme-toggle" id="theme-toggle" aria-label="Toggle theme">
      <span id="theme-icon">☀️</span>
      </button>
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


              // Theme Toggle Functionality
  const themeToggle = document.getElementById('theme-toggle');
  const themeIcon = document.getElementById('theme-icon');
  const htmlElement = document.documentElement;

  // Check for saved theme preference or default to 'light'
  const currentTheme = localStorage.getItem('theme') || 'light';
  htmlElement.setAttribute('data-theme', currentTheme);
  themeIcon.textContent = currentTheme === 'dark' ? '☾️' : '☀️';

  // Toggle theme function
  themeToggle.addEventListener('click', () => {
      const currentTheme = htmlElement.getAttribute('data-theme');
      const newTheme = currentTheme === 'dark' ? 'light' : 'dark';

      htmlElement.setAttribute('data-theme', newTheme);
      localStorage.setItem('theme', newTheme);
      themeIcon.textContent = newTheme === 'dark' ? '☾️' : '☀️';
    });
// Run when hash changes
window.addEventListener('hashchange', filterPosts);
</script>
