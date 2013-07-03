---
layout: index
---

## posts

{% for post in site.posts %}
- {{ post.date | date: "%d %b %Y" }} [{{ post.title }}]({{ post.url }})
{% endfor %}
