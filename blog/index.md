---
title: About 256 Blog and Me
author: Spencer
layout: page
---
I am Spencer and this is my blog. Primarily I am a Flex/Flash developer, but I am trying to get into Android development. I studied at the University of Wisconsin – Stevens Point, with degrees in Web & Digital Media Development and Computer Information Systems. Now I work for [Cru][1], making a cool tool called MPDX.

Hopefully you will find information about all of my current projects on here and you will be able to learn from my mistakes and struggles.

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

   [1]: http://www.cru.org/ (CRU)
