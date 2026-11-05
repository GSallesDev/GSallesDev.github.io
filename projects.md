---
layout: page
title: Projects
permalink: /projects/
---

{% assign lista = site.projects | sort: "order" %}
{% for p in lista %}
<div style="margin-bottom: 2rem;">
  {% if p.cover %}
  <a href="{{ p.url | relative_url }}">
    <img src="{{ p.cover | relative_url }}" alt="{{ p.title }}" loading="lazy">
  </a>
  {% endif %}
  <h2><a href="{{ p.url | relative_url }}">{{ p.title }}</a></h2>
  <p>{{ p.tagline }}</p>
</div>
{% endfor %}
