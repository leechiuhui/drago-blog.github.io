---
layout: page
title: 搜尋
permalink: /search/
---

<div class="search-page">
  <h1>搜尋文章</h1>
  <p>在這裡搜尋您感興趣的內容</p>

  <div class="search-container">
    <div class="search-box">
      <input type="text" id="search-input" placeholder="輸入關鍵字搜尋文章..." autocomplete="off">
      <button type="button" id="search-button">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <circle cx="11" cy="11" r="8"></circle>
          <path d="m21 21-4.35-4.35"></path>
        </svg>
      </button>
    </div>
    <div class="search-stats" id="search-stats"></div>
  </div>

  <div class="search-results" id="search-results">
    <div class="no-results" id="no-results" style="display: none;">
      <div class="no-results-icon">🔍</div>
      <h3>找不到相關文章</h3>
      <p>請嘗試使用不同的關鍵字</p>
    </div>
  </div>

  <div class="all-posts" id="all-posts">
    <h2>所有文章</h2>
    <div class="posts-grid">
      {% for post in site.posts %}
        <article class="post-card" data-title="{{ post.title | downcase }}" data-content="{{ post.content | strip_html | downcase }}" data-tags="{{ post.tags | join: ' ' | downcase }}" data-categories="{{ post.categories | join: ' ' | downcase }}">
          <div class="post-card-header">
            <h3 class="post-title">
              <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
            </h3>
            <time class="post-date" datetime="{{ post.date | date_to_xmlschema }}">
              {{ post.date | date: "%Y-%m-%d" }}
            </time>
          </div>
          
          <div class="post-meta">
            {% if post.categories.size > 0 %}
              <div class="post-categories">
                {% for category in post.categories %}
                  <span class="category">{{ category }}</span>
                {% endfor %}
              </div>
            {% endif %}
            
            {% if post.tags.size > 0 %}
              <div class="post-tags">
                {% for tag in post.tags %}
                  <span class="tag">{{ tag }}</span>
                {% endfor %}
              </div>
            {% endif %}
          </div>
          
          {% if post.excerpt %}
            <div class="post-excerpt">
              {{ post.excerpt | strip_html | truncatewords: 30 }}
            </div>
          {% endif %}
        </article>
      {% endfor %}
    </div>
  </div>
</div>

<style>
.search-page {
  max-width: 900px;
  margin: 0 auto;
}

.search-container {
  margin: 2rem 0;
}

.search-box {
  position: relative;
  max-width: 600px;
  margin: 0 auto;
}

.search-box input {
  width: 100%;
  padding: 1rem 3rem 1rem 1.5rem;
  font-size: 1.1rem;
  border: 2px solid #e2e8f0;
  border-radius: 50px;
  background: white;
  transition: all 0.3s ease;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.search-box input:focus {
  outline: none;
  border-color: #2563eb;
  box-shadow: 0 4px 20px rgba(37, 99, 235, 0.2);
}

.search-box button {
  position: absolute;
  right: 0.5rem;
  top: 50%;
  transform: translateY(-50%);
  background: #2563eb;
  color: white;
  border: none;
  border-radius: 50%;
  width: 2.5rem;
  height: 2.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.search-box button:hover {
  background: #1d4ed8;
}

.search-stats {
  text-align: center;
  margin-top: 1rem;
  color: #64748b;
  font-size: 0.9rem;
}

.search-results {
  margin: 2rem 0;
}

.no-results {
  text-align: center;
  padding: 3rem 1rem;
  color: #64748b;
}

.no-results-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.no-results h3 {
  margin-bottom: 0.5rem;
  color: #374151;
}

.posts-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 1.5rem;
  margin-top: 1.5rem;
}

.post-card {
  background: white;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.5rem;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.post-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, #2563eb, #3b82f6, #60a5fa);
  transform: scaleX(0);
  transition: transform 0.3s ease;
}

.post-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
}

.post-card:hover::before {
  transform: scaleX(1);
}

.post-card-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 1rem;
  gap: 1rem;
}

.post-title {
  margin: 0;
  font-size: 1.2rem;
  font-weight: 600;
  line-height: 1.4;
  flex: 1;
}

.post-title a {
  color: #1f2937;
  text-decoration: none;
  transition: color 0.2s ease;
}

.post-title a:hover {
  color: #2563eb;
}

.post-date {
  color: #64748b;
  font-size: 0.85rem;
  white-space: nowrap;
  background: #f1f5f9;
  padding: 0.25rem 0.75rem;
  border-radius: 20px;
}

.post-meta {
  margin-bottom: 1rem;
}

.post-categories, .post-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 0.5rem;
}

.category {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 0.25rem 0.75rem;
  border-radius: 6px;
  font-size: 0.75rem;
  font-weight: 500;
}

.tag {
  background: #f1f5f9;
  color: #64748b;
  padding: 0.25rem 0.75rem;
  border-radius: 15px;
  font-size: 0.75rem;
  font-weight: 500;
  border: 1px solid #e2e8f0;
}

.post-excerpt {
  color: #64748b;
  line-height: 1.6;
  font-size: 0.95rem;
}

.highlight {
  background: #fef3c7;
  padding: 0.1rem 0.2rem;
  border-radius: 3px;
}

@media (max-width: 768px) {
  .posts-grid {
    grid-template-columns: 1fr;
  }
  
  .post-card {
    padding: 1rem;
  }
  
  .post-card-header {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.5rem;
  }
  
  .search-box input {
    padding: 0.875rem 3rem 0.875rem 1rem;
    font-size: 1rem;
  }
}
</style>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const searchInput = document.getElementById('search-input');
  const searchButton = document.getElementById('search-button');
  const searchStats = document.getElementById('search-stats');
  const searchResults = document.getElementById('search-results');
  const noResults = document.getElementById('no-results');
  const allPosts = document.getElementById('all-posts');
  const postCards = document.querySelectorAll('.post-card');

  let searchTimeout;

  function performSearch() {
    const searchTerm = searchInput.value.toLowerCase().trim();
    
    if (searchTerm === '') {
      showAllPosts();
      return;
    }

    let matchedPosts = [];
    let visibleCount = 0;

    postCards.forEach(function(card) {
      const title = card.getAttribute('data-title');
      const content = card.getAttribute('data-content');
      const tags = card.getAttribute('data-tags');
      const categories = card.getAttribute('data-categories');
      
      const searchableText = title + ' ' + content + ' ' + tags + ' ' + categories;
      
      if (searchableText.includes(searchTerm)) {
        card.style.display = 'block';
        visibleCount++;
        
        // 高亮搜尋關鍵字
        highlightSearchTerm(card, searchTerm);
        matchedPosts.push(card);
      } else {
        card.style.display = 'none';
      }
    });

    updateSearchStats(searchTerm, visibleCount);
    
    if (visibleCount === 0) {
      showNoResults();
    } else {
      hideNoResults();
    }
  }

  function highlightSearchTerm(card, term) {
    const titleElement = card.querySelector('.post-title a');
    const excerptElement = card.querySelector('.post-excerpt');
    
    if (titleElement) {
      const titleText = titleElement.textContent;
      const highlightedTitle = titleText.replace(
        new RegExp(term, 'gi'),
        '<span class="highlight">$&</span>'
      );
      titleElement.innerHTML = highlightedTitle;
    }
    
    if (excerptElement) {
      const excerptText = excerptElement.textContent;
      const highlightedExcerpt = excerptText.replace(
        new RegExp(term, 'gi'),
        '<span class="highlight">$&</span>'
      );
      excerptElement.innerHTML = highlightedExcerpt;
    }
  }

  function removeHighlights() {
    postCards.forEach(function(card) {
      const titleElement = card.querySelector('.post-title a');
      const excerptElement = card.querySelector('.post-excerpt');
      
      if (titleElement) {
        titleElement.innerHTML = titleElement.textContent;
      }
      
      if (excerptElement) {
        excerptElement.innerHTML = excerptElement.textContent;
      }
    });
  }

  function updateSearchStats(term, count) {
    if (term) {
      searchStats.textContent = `找到 ${count} 篇包含 "${term}" 的文章`;
    } else {
      searchStats.textContent = '';
    }
  }

  function showAllPosts() {
    removeHighlights();
    postCards.forEach(function(card) {
      card.style.display = 'block';
    });
    searchStats.textContent = '';
    hideNoResults();
  }

  function showNoResults() {
    noResults.style.display = 'block';
  }

  function hideNoResults() {
    noResults.style.display = 'none';
  }

  // 搜尋事件監聽
  searchInput.addEventListener('input', function() {
    clearTimeout(searchTimeout);
    searchTimeout = setTimeout(performSearch, 300);
  });

  searchButton.addEventListener('click', performSearch);

  searchInput.addEventListener('keypress', function(e) {
    if (e.key === 'Enter') {
      performSearch();
    }
  });

  // 初始化
  hideNoResults();
});
</script> 