---
layout: page
title: Assignments
permalink: /assignments/
---

This page lists the assignments, which are major steps in the term project:

{% assign assignments = site.posts | where: "categories", "assignments" %}

| Title and Link | Assigned Date | Due Date |
| ------ | ------ | ------ |
{% for assignment in assignments %}| [{{ assignment.title }}]({{ assignment.url | relative_url }}) | {{ assignment.assigned | date: "%e %B %Y" | lstrip }} | {{ assignment.due | date: "%e %B %Y" | lstrip }} |
{% endfor %}