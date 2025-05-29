---
layout: page
title: 標籤
permalink: /tags/
---

# 標籤

## 所有標籤（Tags）

{% assign all_tags = '' %}
{% for post in site.posts %}
  {% for tag in post.tags %}
    {% unless all_tags contains tag %}
      {% assign all_tags = all_tags | append: tag | append: ',' %}
    {% endunless %}
  {% endfor %}
{% endfor %}

{% assign tag_array = all_tags | split: ',' | sort %}
{% for tag in tag_array %}
  {% if tag != '' %}
* {{ tag }}
  {% endif %}
{% endfor %} 