---
layout: default
title: "Diary"
---

# Diary

<div class="feed-list">
{% for post in site.posts %}
  <a class="feed-card" href="{{ post.url | relative_url }}">
    {% if post.image %}
      <img class="feed-thumb" src="{{ post.image | relative_url }}" alt="{{ post.caption | default: post.title }}">
    {% elsif post.images and post.images.size > 0 %}
      <img class="feed-thumb" src="{{ post.images[0].thumb | default: post.images[0].full | relative_url }}" alt="{{ post.images[0].alt | default: post.title }}">
    {% else %}
      <img class="feed-thumb" src="https://via.placeholder.com/300x200?text=No+Image" alt="">
    {% endif %}
    <div class="feed-body">
      <div class="feed-title">{{ post.title }}</div>
      <div class="feed-meta">
        {{ post.date | date: "%B %d, %Y" }}
        {%- if post.location -%} • {{ post.location }}{%- endif -%}
      </div>
      {% if post.caption %}
        <div class="feed-caption">{{ post.caption }}</div>
      {% endif %}
    </div>
  </a>
{% endfor %}
</div>
