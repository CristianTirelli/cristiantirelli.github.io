---
title: "Images"
permalink: /images/
layout: single
classes: wide
author_profile: true
---

{% assign pics = site.portfolio | where: "portfolio_type", "images" | reverse %}

<div class="grid__wrapper images-grid">
  {% for post in pics %}
    <div class="archive__item image-card">

      <h2 class="archive__item-title image-title">
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h2>

      {% if post.excerpt %}
        <p class="archive__item-excerpt image-excerpt">{{ post.excerpt }}</p>
      {% endif %}

      <a href="{{ post.url | relative_url }}" class="image-thumb">
        <img src="{{ post.header.teaser | relative_url }}"
             alt="{{ post.title }}"
             loading="lazy">
      </a>

    </div>
  {% endfor %}
</div>
