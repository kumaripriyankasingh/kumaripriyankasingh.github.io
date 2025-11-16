---
layout: blogpage
title: Blogs
permalink: /blogs/
---

<div class="posts-list">
  <ul>
    {% for post in site.posts %}
      <li>
        <a class="post-link" href="{{ post.url }}">{{ post.title }}</a>
      </li>
    {% endfor %}
  </ul>
</div>