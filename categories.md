---
layout: page
title: 分類
permalink: /categories/
---

# 文章分類

<div class="categories-list">
{% assign categories = site.categories | sort %}
{% for category in categories %}
  <div class="category-item">
    <h3 id="{{ category[0] | slugify }}">
      <a href="#{{ category[0] | slugify }}">{{ category[0] }}</a>
      <span class="post-count">({{ category[1].size }})</span>
    </h3>
    <ul class="post-list">
    {% for post in category[1] %}
      <li>
        <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </li>
    {% endfor %}
    </ul>
  </div>
{% endfor %}
</div>

<style>
.categories-list {
  margin-top: 2rem;
}

.category-item {
  margin-bottom: 2rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid #eee;
}

.category-item h3 {
  color: #2a7ae4;
  margin-bottom: 1rem;
}

.post-count {
  color: #666;
  font-size: 0.9em;
  font-weight: normal;
}

.post-list {
  list-style: none;
  padding-left: 0;
}

.post-list li {
  margin-bottom: 0.5rem;
  display: flex;
  align-items: center;
}

.post-date {
  color: #666;
  font-size: 0.9em;
  margin-right: 1rem;
  min-width: 100px;
}

.post-list a {
  text-decoration: none;
  color: #333;
}

.post-list a:hover {
  color: #2a7ae4;
  text-decoration: underline;
}
</style> 