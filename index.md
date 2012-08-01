---
layout: page
title: Hello World!
tagline: Supporting tagline
---
{% include JB/setup %}

* 1
* 2
* 2


<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>


{% for post in site.posts limit: 2 %}  
{% endfor %}
