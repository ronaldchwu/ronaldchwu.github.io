---
title: "Writing"
permalink: /writing/
layout: archive
author_profile: true
---

{% assign posts = site.categories['Writing'] %}
{% for post in posts %}
  {% include archive-single.html type="list" %}
{% endfor %}