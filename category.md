---
layout: default
title: Category
permalink: /category/
---

<div class="home">
  <h1 class="page-heading">Category</h1>
  <ul class="post-list">
{% capture categories %}{% for category in site.categories %}{{ category | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
{% assign category = categories | split:',' | sort %}
{% for item in (0..site.categories.size) %}{% unless forloop.last %}
{% capture word %}{{ category[item] | strip_newlines }}{% endcapture %}
<h2 class="category" id="{{ word }}">{{ word | upcase }}</h2>
<ul>
{% for post in site.categories[word] %}{% if post.title != null %}
<li><span>{{ post.date | date: "%b %d" }}</span> » <a href="{{ site.baseurl}}{{ post.url }}">{{ post.title }}</a></li>
{% endif %}{% endfor %}
</ul>
{% endunless %}{% endfor %}
  </ul>
</div>