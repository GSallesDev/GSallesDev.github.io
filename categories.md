---
layout: page
title: Categories
permalink: /categories/
---

{% for category in site.categories %}
<h2>{{ category[0] }}</h2>
<ul>
  {% for post in category[1] %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <small>{{ post.date | date: "%d/%m/%Y" }}</small>
  </li>
  {% endfor %}
</ul>
{% endfor %}
