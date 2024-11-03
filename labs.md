---
layout: page
title: Labs
permalink: /labs/
---

This page lists the lab activities:

{% assign labs_list = site.posts | where: "categories", "labs" | sort: due %}

| Title and Link | Due Date |
| ------ | ------ |
{% for lab in labs_list %}| [{{ lab.title }}]({{ lab.url | relative_url }}) | {{ lab.due | date: "%e %B %Y" | lstrip }} |
{% endfor %}
