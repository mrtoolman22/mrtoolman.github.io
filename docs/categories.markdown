---
layout: page
title: Danh mục
permalink: /categories/
---

<div>
  {% for category in site.categories %}
    <h3 id="{{ category[0] }}">{{ category[0] }}</h3>
    <ul>
      {% for post in category[1] %}
        <li>
          <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
          <small>{{ post.date | date_to_string }}</small>
        </li>
      {% endfor %}
    </ul>
  {% endfor %}
</div>