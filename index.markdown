---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
title: "Drago Blog"
---

<div class="home-header">
  <h1 class="page-heading">Drago Blog</h1>
  <p class="page-description">歡迎來到我的個人部落格，分享生活、技術與心得</p>
</div>

<div class="search-container">
  <input type="text" id="search-input" class="search-input" placeholder="搜尋文章...">
</div>

<div class="latest-posts">
  <h2>最新文章</h2>
  
  <div class="post-list">
    {% for post in site.posts limit:10 %}
      <article class="post-item">
        <h3 class="post-title">
          <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
        </h3>
        
        <div class="post-meta">
          <time datetime="{{ post.date | date_to_xmlschema }}">
            {{ post.date | date: "%Y-%m-%d" }}
          </time>
          
          {% if post.categories.size > 0 %}
            <span class="post-categories">
              {% for category in post.categories %}
                <a href="{{ '/categories/' | append: category | relative_url }}" class="category">{{ category }}</a>
              {% endfor %}
            </span>
          {% endif %}
          
          {% if post.tags.size > 0 %}
            <span class="post-tags">
              {% for tag in post.tags %}
                <a href="{{ '/tags/' | append: tag | relative_url }}" class="tag">{{ tag }}</a>
              {% endfor %}
            </span>
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

<script>
// 簡單的搜尋功能
document.addEventListener('DOMContentLoaded', function() {
  const searchInput = document.getElementById('search-input');
  const postItems = document.querySelectorAll('.post-item');
  
  searchInput.addEventListener('input', function() {
    const searchTerm = this.value.toLowerCase();
    
    postItems.forEach(function(item) {
      const title = item.querySelector('.post-title').textContent.toLowerCase();
      const excerpt = item.querySelector('.post-excerpt');
      const excerptText = excerpt ? excerpt.textContent.toLowerCase() : '';
      
      if (title.includes(searchTerm) || excerptText.includes(searchTerm)) {
        item.style.display = 'block';
      } else {
        item.style.display = 'none';
      }
    });
  });
});
</script>
