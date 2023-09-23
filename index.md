---
layout: default
title: NES Emulator Development Blog
---

This is my blog site for NES Emulator that I have been writing.
Go ahead and check my emulator on github.<br>
[Famulator Famicom/NES Emulator](https://github.com/tsubo164/Famulator)

<ul>
  {% for post in site.posts %}
    <li>
      {{ post.date | date: "%Y-%m-%d" }} <a href="{{ post.url | absolute_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
