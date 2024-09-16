---
layout: page
title: Lab Questions
permalink: /labs/
---

This page lists the lab activities:

{% assign labs_list = site.posts | where: "categories", "labs" %}

| Title and Link | Due Date |
| ------ | ------ |
{% for lab in labs_list %}| [{{ lab.title }}]({{ site.url }}{{ lab.url }}) | {{ lab.due | date: "%e %B %Y" | lstrip }} |
{% endfor %}
