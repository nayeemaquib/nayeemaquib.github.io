---
layout: page
title: Blog
---

<br>

<ul>
  {% for post in site.texts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
