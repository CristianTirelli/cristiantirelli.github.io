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
.images-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 0.9rem;
  align-items: start;
}

/* Card styling & hover effects */
.images-grid .image-card {
  position: relative; /* Required for the overlay */
  border: 1px solid #ddd;
  border-radius: 12px;
  padding: 0.8rem;
  box-shadow: 0 1px 3px rgba(0,0,0,0.08);
  transition: transform 0.15s ease, box-shadow 0.15s ease;
}

.images-grid .image-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.12);
}

/* Tighter spacing */
.images-grid .image-title { margin: 0 0 0.15rem 0; }
.images-grid .image-excerpt { margin: 0 0 0.35rem 0; }

/* Fixed-size thumbnails */
.images-grid .image-thumb {
  display: block;
  width: 100%;
  height: 180px;
  overflow: hidden;
  border-radius: 10px;
}

.images-grid .image-thumb img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* CRITICAL FIX: Full clickable layer sits on top of everything */
.images-grid .card-overlay {
  position: absolute;
  inset: 0;
  z-index: 10; /* Higher than elements inside */
  cursor: pointer;
}
</style>

{% assign pics = site.portfolio | where: "portfolio_type", "images" | sort: "title" %}

<div class="images-grid">
  {% for post in pics %}

    <div class="archive__item image-card">

      <a href="{{ post.url | relative_url }}" class="card-overlay" aria-label="{{ post.title }}"></a>

      <h2 class="archive__item-title image-title">
        {{ post.title }}
      </h2>

      {% if post.excerpt %}
        <p class="archive__item-excerpt image-excerpt">{{ post.excerpt }}</p>
      {% endif %}

      <div class="image-thumb">
        <img src="{{ post.header.teaser | relative_url }}"
            alt="{{ post.title }}"
            loading="lazy">
      </div>

    </div>

  {% endfor %}
</div>