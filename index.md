---
layout: default
title: NES Emulator Development Blog
---

This is my blog site for NES Emulator that I have been writing.

<ul>
  {% for post in site.posts %}
    <li>
      {{ post.date | date: %y-%m-%d }} <a href="{{ post.url | absolute_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
