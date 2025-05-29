---
layout: page
title: 搜尋
permalink: /search/
---

# 站內搜尋

<div class="search-container">
  <input type="text" id="search-input" placeholder="輸入關鍵字搜尋文章..." />
  <button id="search-button">🔍</button>
</div>

<div id="search-results">
  <p id="search-info">請輸入關鍵字開始搜尋</p>
  <ul id="results-list"></ul>
</div>

<script>
// 搜尋功能
document.addEventListener('DOMContentLoaded', function() {
  const searchInput = document.getElementById('search-input');
  const searchButton = document.getElementById('search-button');
  const searchInfo = document.getElementById('search-info');
  const resultsList = document.getElementById('results-list');
  
  // 文章資料
  const posts = [
    {% for post in site.posts %}
    {
      title: "{{ post.title | escape }}",
      url: "{{ post.url | relative_url }}",
      date: "{{ post.date | date: '%Y-%m-%d' }}",
      categories: [{% for category in post.categories %}"{{ category }}"{% unless forloop.last %},{% endunless %}{% endfor %}],
      tags: [{% for tag in post.tags %}"{{ tag }}"{% unless forloop.last %},{% endunless %}{% endfor %}],
      content: "{{ post.content | strip_html | escape | truncate: 200 }}"
    }{% unless forloop.last %},{% endunless %}
    {% endfor %}
  ];
  
  function performSearch() {
    const query = searchInput.value.toLowerCase().trim();
    
    if (query === '') {
      searchInfo.textContent = '請輸入關鍵字開始搜尋';
      resultsList.innerHTML = '';
      return;
    }
    
    const results = posts.filter(post => {
      return post.title.toLowerCase().includes(query) ||
             post.content.toLowerCase().includes(query) ||
             post.categories.some(cat => cat.toLowerCase().includes(query)) ||
             post.tags.some(tag => tag.toLowerCase().includes(query));
    });
    
    if (results.length === 0) {
      searchInfo.textContent = `沒有找到包含 "${query}" 的文章`;
      resultsList.innerHTML = '';
    } else {
      searchInfo.textContent = `找到 ${results.length} 篇相關文章：`;
      resultsList.innerHTML = results.map(post => `
        <li class="search-result-item">
          <h4><a href="${post.url}">${post.title}</a></h4>
          <p class="search-meta">
            <span class="search-date">${post.date}</span>
            ${post.categories.length > 0 ? `<span class="search-categories">分類: ${post.categories.join(', ')}</span>` : ''}
            ${post.tags.length > 0 ? `<span class="search-tags">標籤: ${post.tags.join(', ')}</span>` : ''}
          </p>
          <p class="search-excerpt">${post.content}</p>
        </li>
      `).join('');
    }
  }
  
  searchButton.addEventListener('click', performSearch);
  searchInput.addEventListener('keypress', function(e) {
    if (e.key === 'Enter') {
      performSearch();
    }
  });
  
  // 即時搜尋
  searchInput.addEventListener('input', function() {
    if (this.value.length > 2) {
      performSearch();
    }
  });
});
</script>

<style>
.search-container {
  display: flex;
  margin: 2rem 0;
  max-width: 600px;
}

#search-input {
  flex: 1;
  padding: 1rem;
  border: 2px solid #ddd;
  border-radius: 8px 0 0 8px;
  font-size: 1rem;
  outline: none;
}

#search-input:focus {
  border-color: #2a7ae4;
}

#search-button {
  padding: 1rem 1.5rem;
  background: #2a7ae4;
  color: white;
  border: none;
  border-radius: 0 8px 8px 0;
  cursor: pointer;
  font-size: 1rem;
}

#search-button:hover {
  background: #1e5bb8;
}

#search-results {
  margin-top: 2rem;
}

#search-info {
  color: #666;
  font-style: italic;
  margin-bottom: 1rem;
}

#results-list {
  list-style: none;
  padding: 0;
}

.search-result-item {
  margin-bottom: 2rem;
  padding: 1.5rem;
  border: 1px solid #eee;
  border-radius: 8px;
  background: #fafafa;
}

.search-result-item h4 {
  margin: 0 0 0.5rem 0;
}

.search-result-item h4 a {
  color: #2a7ae4;
  text-decoration: none;
}

.search-result-item h4 a:hover {
  text-decoration: underline;
}

.search-meta {
  color: #666;
  font-size: 0.9em;
  margin: 0.5rem 0;
}

.search-meta span {
  margin-right: 1rem;
}

.search-excerpt {
  color: #555;
  line-height: 1.6;
  margin: 0.5rem 0 0 0;
}
</style> 