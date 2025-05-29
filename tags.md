---
layout: page
title: 標籤
permalink: /tags/
---

<div class="tags-page">
  <h1>標籤</h1>
  <p>透過標籤探索不同主題的文章</p>

  <!-- 標籤雲 -->
  <div class="tag-cloud">
    {% assign tags = site.tags | sort %}
    {% for tag in tags %}
      <a href="#{{ tag[0] | slugify }}" class="tag" data-count="{{ tag[1].size }}">
        {{ tag[0] }} ({{ tag[1].size }})
      </a>
    {% endfor %}
  </div>

  <!-- 按標籤分組的文章列表 -->
  <div class="tag-sections">
    {% for tag in tags %}
      <div class="tag-section" id="{{ tag[0] | slugify }}">
        <h2 class="tag-title">{{ tag[0] }}</h2>
        <div class="tag-posts">
          {% for post in tag[1] %}
            <article class="tag-post-item">
              <h3 class="post-title">
                <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
              </h3>
              <div class="post-meta">
                <time datetime="{{ post.date | date_to_xmlschema }}">
                  {{ post.date | date: "%Y-%m-%d" }}
                </time>
                {% if post.categories.size > 0 %}
                  <span class="post-categories">
                    {% for category in post.categories %}
                      <span class="category">{{ category }}</span>
                    {% endfor %}
                  </span>
                {% endif %}
              </div>
              {% if post.excerpt %}
                <div class="post-excerpt">
                  {{ post.excerpt | strip_html | truncatewords: 20 }}
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
.tags-page {
  max-width: 800px;
  margin: 0 auto;
}

.tag-cloud {
  margin: 2rem 0;
  padding: 2rem;
  background: #f8fafc;
  border-radius: 8px;
  border: 1px solid #e2e8f0;
}

.tag-cloud .tag {
  margin: 0.25rem;
  font-size: 0.875rem;
}

.tag-sections {
  margin-top: 3rem;
}

.tag-section {
  margin-bottom: 3rem;
  padding-bottom: 2rem;
  border-bottom: 1px solid #e2e8f0;
}

.tag-section:last-child {
  border-bottom: none;
}

.tag-title {
  font-size: 1.5rem;
  font-weight: 600;
  color: #2563eb;
  margin-bottom: 1rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #e2e8f0;
}

.tag-posts {
  display: grid;
  gap: 1rem;
}

.tag-post-item {
  padding: 1rem;
  background: white;
  border: 1px solid #e2e8f0;
  border-radius: 6px;
  transition: box-shadow 0.2s ease;
}

.tag-post-item:hover {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.tag-post-item .post-title {
  font-size: 1.125rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.tag-post-item .post-title a {
  color: #1f2937;
  text-decoration: none;
}

.tag-post-item .post-title a:hover {
  color: #2563eb;
}

.tag-post-item .post-meta {
  color: #64748b;
  font-size: 0.875rem;
  margin-bottom: 0.5rem;
}

.tag-post-item .post-excerpt {
  color: #64748b;
  line-height: 1.6;
}

.tag-post-item .category {
  background: #f1f5f9;
  color: #64748b;
  padding: 0.125rem 0.5rem;
  border-radius: 4px;
  font-size: 0.75rem;
  margin-left: 0.5rem;
}

@media (max-width: 768px) {
  .tag-cloud {
    padding: 1rem;
  }
  
  .tag-post-item {
    padding: 0.75rem;
  }
}
</style>

<script>
document.addEventListener('DOMContentLoaded', function() {
  // 平滑滾動到標籤區塊
  const tagLinks = document.querySelectorAll('.tag-cloud .tag');
  
  tagLinks.forEach(function(link) {
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