---
layout: default
avatar: false
permalink: /
---

{% for post in site.posts limit: 2 %}
<h3><a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h3>
<span class="post-meta">{{ post.date | date: "%Y, %b %d" }}</span>
<p class="description">{% if post.description %}{{ post.description | strip_html | strip_newlines | truncate: 250 }}{% else %}{{ post.content | strip_html | strip_newlines | truncate: 250 }}{% endif %}</p>

---

{% endfor %}

<a class="trigger" style="float:right" href="/blog">更多&nbsp;&nbsp;&gt;&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</a>