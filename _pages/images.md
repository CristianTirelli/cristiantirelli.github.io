---
title: "Just some random pictures"
permalink: /images/
layout: single
classes:
  - wide
  - images-page
author_profile: true
---

<style>
/* Only affects this page because it's embedded here */
.images-grid{
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 0.9rem;
  align-items: start;
}

/* tighter spacing */
.images-grid .image-title{ margin: 0 0 0.15rem 0; }
.images-grid .image-excerpt{ margin: 0 0 0.35rem 0; }

/* fixed-size thumbnails */
.images-grid .image-thumb{
  display:block;
  width:100%;
  height:180px;          /* <-- change this number */
  overflow:hidden;
  border-radius: 10px;
}

.images-grid .image-thumb img{
  width:100%;
  height:100%;
  object-fit:cover;       /* crops nicely */
  display:block;
}
</style>

{% assign pics = site.portfolio | where: "portfolio_type", "images" | reverse %}

<div class="images-grid">
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
