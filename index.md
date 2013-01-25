---
layout: page
title: ~rlankenau/ 
---
{% include JB/setup %}

<ul class="posts">
  {% for post in site.posts %}
    <li>
	<span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
	<div>{{ post.content | truncatewords:200</div>
	</li>
  {% endfor %}
</ul>


