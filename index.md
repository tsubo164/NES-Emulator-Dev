---
layout: default
title: NES Emulator Development Blog
---

This is my blog site for NES Emulator that I have been writing.

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>