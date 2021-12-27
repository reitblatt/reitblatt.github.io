---
title: Posts
layout: archive
permalink: /posts/
author_profile: true
---

{% for post in site.posts limit: 5 %}
   {% unless post.hidden %}
      {% include archive-single.html %}
   {% endunless %}
{% endfor %}