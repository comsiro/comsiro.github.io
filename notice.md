---
layout: page
title: 공지
permalink: /notice/
---

  <ul class="post-list">
    {% for post in site.posts %}
      {% if post.categories contains "notice" %}
      <li>
        {% assign date_format = site.minima.date_format | default: "%b %-d, %Y" %}
        <span class="post-meta">{{ post.date | date: date_format }}</span>

        <h2>
          <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
        </h2>
      </li>
      {% endif %}
    {% endfor %}
  </ul>