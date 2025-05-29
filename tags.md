---
layout: page
title: 標籤
permalink: /tags/
---

# 文章標籤

<div class="tags-cloud">
{% assign tags = site.tags | sort %}
{% for tag in tags %}
  <a href="#{{ tag[0] | slugify }}" class="tag-link" data-count="{{ tag[1].size }}">
    {{ tag[0] }} ({{ tag[1].size }})
  </a>
{% endfor %}
</div>

<div class="tags-list">
{% for tag in tags %}
  <div class="tag-item">
    <h3 id="{{ tag[0] | slugify }}">
      <a href="#{{ tag[0] | slugify }}">{{ tag[0] }}</a>
      <span class="post-count">({{ tag[1].size }})</span>
    </h3>
    <ul class="post-list">
    {% for post in tag[1] %}
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
.tags-cloud {
  margin: 2rem 0;
  padding: 1rem;
  background: #f8f9fa;
  border-radius: 8px;
  text-align: center;
}

.tag-link {
  display: inline-block;
  margin: 0.25rem;
  padding: 0.5rem 1rem;
  background: #e9ecef;
  color: #495057;
  text-decoration: none;
  border-radius: 20px;
  font-size: 0.9em;
  transition: all 0.3s ease;
}

.tag-link:hover {
  background: #2a7ae4;
  color: white;
  transform: translateY(-2px);
}

.tag-link[data-count="1"] { font-size: 0.8em; }
.tag-link[data-count="2"] { font-size: 0.9em; }
.tag-link[data-count="3"] { font-size: 1em; }
.tag-link[data-count="4"] { font-size: 1.1em; }
.tag-link[data-count="5"] { font-size: 1.2em; }

.tags-list {
  margin-top: 3rem;
}

.tag-item {
  margin-bottom: 2rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid #eee;
}

.tag-item h3 {
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