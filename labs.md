---
layout: page
title: Labs
permalink: /labs/
---

This page lists the lab activities:

{% assign labs_list = site.posts | where: "categories", "labs" %}
{% for lab in labs_list %}
* [{{ lab.title }}]({{ lab.url }}) {{ lab.date | date: "%e %B %Y" | lstrip }}
{% endfor %}