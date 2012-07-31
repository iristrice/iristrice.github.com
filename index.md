---
layout: page
title: Iris的博客
tagline: 瞎搞的
---
{% include JB/setup %}


In `_config.yml` remember to specify your own data:

---
***

        sdafdasf
        asdf
        asdf

---
```javascript
<table>
<tr>
<td>Foo</td>
<td>Foo</td>
<td>Foo</td>
<td>Foo</td>
</tr>
<tr>
<td>Foo</td>
</tr>
</table>
```

## Sample Posts

This blog contains sample posts which help stage pages and blog data.
When you don't need the samples anymore just delete the `_posts/core-samples` folder.

    $ rm -rf _posts/core-samples

Here's a sample "posts list".

<ul class="posts">
{% for post in site.posts %}
<li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>

## To-Do

