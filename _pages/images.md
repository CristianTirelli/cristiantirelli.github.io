---
title: "Images"
permalink: /images/
layout: single
classes: wide
author_profile: true
---

{% assign pics = site.portfolio | where: "portfolio_type", "images" | reverse %}

<div class="grid__wrapper">
  {% for post in pics %}
    <div class="archive__item">
      <a href="{{ post.url | relative_url }}" class="archive__item-teaser">
        <img src="{{ post.header.teaser | relative_url }}" alt="{{ post.title }}">
      </a>

      <h2 class="archive__item-title">
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h2>

      {% if post.excerpt %}
        <p class="archive__item-excerpt">{{ post.excerpt }}</p>
      {% endif %}
    </div>
  {% endfor %}
</div>
