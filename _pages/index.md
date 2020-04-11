---
layout: default
avatar: false
permalink: /
---
## 🚀 BLOG
You can use this page to showcase your work, portfolio/project, your Latest post {% for post in site.posts limit: 1 %}<a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>{% endfor %} or another stuff that you love to share to the world.

---

{% for post in site.posts limit: 2 %}
<h3><a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h3>
<span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
<p class="description">{% if post.description %}{{ post.description | strip_html | strip_newlines | truncate: 250 }}{% else %}{{ post.content | strip_html | strip_newlines | truncate: 250 }}{% endif %}</p>

---

{% endfor %}

<div class="wrapper"><a class="trigger" href="/blog">更多&lt;&lt;</a></div>