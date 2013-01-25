---
layout: page
title: ~rlankenau/ 
---
{% include JB/setup %}

<ul class="posts">
  {% for post in paginator.posts %}
    <li>
	<H2>{{ post.title }}</H2> 
	<div>{{ post.date | date_to_string }}</div>
	<div>{{ post.content }}</div>
	<div><a href="{{ BASE_PATH }}{{ post.url }}">Comment</a></div>
	</li>
  {% endfor %}
</ul>
<!-- Pagination links -->
<div class="pagination">
  {% if paginator.previous_page %}
    <a href="/page{{paginator.previous_page}}" class="previous">Newer Posts</a>
  {% endif %}
  <span class="page_number ">Page: {{paginator.page}} of {{paginator.total_pages}}</span>
  {% if paginator.next_page %}
    <a href="/page{{paginator.next_page}}" class="next ">Older Posts</a>
  {% endif %}
</div>

