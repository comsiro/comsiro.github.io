---
layout: page
title: Devops
permalink: /devops/
---

  <ul class="post-list">
    {% for post in site.posts %}
      {% if post.categories contains "devops" %}
      <li>
        {% assign date_format = site.minima.date_format | default: "%b %-d, %Y" %}
        <span class="post-meta">{{ post.date | date: date_format }}</span>

        <h2>
          <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
        </h2>
      </li>
      <hr>
      {% endif %}
    {% endfor %}
  </ul>