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

/* NEW: card styling */
.images-grid .image-card{
  border: 1px solid #ddd;
  border-radius: 12px;
  padding: 0.8rem;
  box-shadow: 0 1px 3px rgba(0,0,0,0.08);
}

.images-grid .image-card{
  border: 1px solid #ddd;
  border-radius: 12px;
  padding: 0.8rem;
  box-shadow: 0 1px 3px rgba(0,0,0,0.08);
  transition: transform 0.15s ease, box-shadow 0.15s ease;
}

.images-grid .image-card:hover{
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.12);
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

.images-grid .image-card-link{
  text-decoration: none;
  color: inherit;
  display: block;
}

/* your existing card style goes here */
.images-grid .image-card{
  border: 1px solid #ddd;
  border-radius: 12px;
  padding: 0.8rem;
  background: #fff;
  height: 100%;
  transition: transform 0.15s ease, box-shadow 0.15s ease;
}

.images-grid .image-card-link:hover .image-card{
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.12);
}
</style>

{% assign pics = site.portfolio | where: "portfolio_type", "images" |  sort: "title" %}

<div class="images-grid">

  
    {% for post in pics %}

<a href="{{ post.url | relative_url }}" class="image-card-link">

  <div class="archive__item image-card">

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

</a>

{% endfor %}
  {% endfor %}
</div>
