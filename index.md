---
layout: page
title: ~rlankenau/ 
---
{% include JB/setup %}

<ul class="posts">
  {% for post in site.posts %}
    <li>
	<H2>{{ post.title }}</H2> 
	<div>{{ post.date | date_to_string }}</div>
	<div>{{ post.content }}</div>
	<div><a href="{{ BASE_PATH }}{{ post.url }}">Comment</a></div>
	</li>
  {% endfor %}
</ul>


