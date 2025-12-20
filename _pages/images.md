---
title: "Images"
permalink: /images/
layout: archive
classes: wide
author_profile: true
---

{% assign pics = site.portfolio | where: "portfolio_type", "images" | reverse %}

<div class="grid__wrapper">
  {% for post in pics %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
