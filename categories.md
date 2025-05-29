---
layout: page
title: 分類
permalink: /categories/
---

<div class="categories-page">
  <h1>分類</h1>
  <p>按照主題分類瀏覽文章</p>

  <!-- 分類概覽 -->
  <div class="category-overview">
    {% assign categories = site.categories | sort %}
    {% for category in categories %}
      <a href="#{{ category[0] | slugify }}" class="category-card">
        <h3>{{ category[0] }}</h3>
        <span class="post-count">{{ category[1].size }} 篇文章</span>
      </a>
    {% endfor %}
  </div>

  <!-- 分類詳細列表 -->
  <div class="category-sections">
    {% for category in categories %}
      <div class="category-section" id="{{ category[0] | slugify }}">
        <h2 class="category-title">{{ category[0] }}</h2>
        <div class="category-posts">
          {% for post in category[1] %}
            <article class="category-post-item">
              <h3 class="post-title">
                <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
              </h3>
              <div class="post-meta">
                <time datetime="{{ post.date | date_to_xmlschema }}">
                  {{ post.date | date: "%Y-%m-%d" }}
                </time>
                {% if post.tags.size > 0 %}
                  <span class="post-tags">
                    {% for tag in post.tags %}
                      <span class="tag">{{ tag }}</span>
                    {% endfor %}
                  </span>
                {% endif %}
              </div>
              {% if post.excerpt %}
                <div class="post-excerpt">
                  {{ post.excerpt | strip_html | truncatewords: 25 }}
                </div>
              {% endif %}
            </article>
          {% endfor %}
        </div>
      </div>
    {% endfor %}
  </div>
</div>

<style>
.categories-page {
  max-width: 900px;
  margin: 0 auto;
}

.category-overview {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
  margin: 2rem 0 3rem 0;
}

.category-card {
  display: block;
  padding: 1.5rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  text-decoration: none;
  border-radius: 8px;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  text-align: center;
}

.category-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
  color: white;
  text-decoration: none;
}

.category-card:nth-child(2n) {
  background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
}

.category-card:nth-child(3n) {
  background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
}

.category-card:nth-child(4n) {
  background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
}

.category-card h3 {
  margin: 0 0 0.5rem 0;
  font-size: 1.25rem;
  font-weight: 600;
}

.category-card .post-count {
  font-size: 0.875rem;
  opacity: 0.9;
}

.category-sections {
  margin-top: 3rem;
}

.category-section {
  margin-bottom: 3rem;
  padding-bottom: 2rem;
  border-bottom: 1px solid #e2e8f0;
}

.category-section:last-child {
  border-bottom: none;
}

.category-title {
  font-size: 1.75rem;
  font-weight: 600;
  color: #2563eb;
  margin-bottom: 1.5rem;
  padding-bottom: 0.5rem;
  border-bottom: 3px solid #e2e8f0;
  position: relative;
}

.category-title::after {
  content: '';
  position: absolute;
  bottom: -3px;
  left: 0;
  width: 60px;
  height: 3px;
  background: #2563eb;
}

.category-posts {
  display: grid;
  gap: 1.5rem;
}

.category-post-item {
  padding: 1.5rem;
  background: white;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  transition: all 0.2s ease;
  position: relative;
  overflow: hidden;
}

.category-post-item::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 4px;
  height: 100%;
  background: #2563eb;
  transform: scaleY(0);
  transition: transform 0.2s ease;
}

.category-post-item:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transform: translateY(-2px);
}

.category-post-item:hover::before {
  transform: scaleY(1);
}

.category-post-item .post-title {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 0.75rem;
  line-height: 1.4;
}

.category-post-item .post-title a {
  color: #1f2937;
  text-decoration: none;
  transition: color 0.2s ease;
}

.category-post-item .post-title a:hover {
  color: #2563eb;
}

.category-post-item .post-meta {
  color: #64748b;
  font-size: 0.875rem;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.category-post-item .post-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.25rem;
}

.category-post-item .tag {
  background: #f1f5f9;
  color: #64748b;
  padding: 0.125rem 0.5rem;
  border-radius: 12px;
  font-size: 0.75rem;
  font-weight: 500;
}

.category-post-item .post-excerpt {
  color: #64748b;
  line-height: 1.6;
  font-size: 0.95rem;
}

@media (max-width: 768px) {
  .category-overview {
    grid-template-columns: 1fr;
  }
  
  .category-card {
    padding: 1rem;
  }
  
  .category-post-item {
    padding: 1rem;
  }
  
  .category-post-item .post-meta {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>

<script>
document.addEventListener('DOMContentLoaded', function() {
  // 平滑滾動到分類區塊
  const categoryLinks = document.querySelectorAll('.category-card');
  
  categoryLinks.forEach(function(link) {
    link.addEventListener('click', function(e) {
      e.preventDefault();
      const targetId = this.getAttribute('href').substring(1);
      const targetElement = document.getElementById(targetId);
      
      if (targetElement) {
        targetElement.scrollIntoView({
          behavior: 'smooth',
          block: 'start'
        });
      }
    });
  });
});
</script> 