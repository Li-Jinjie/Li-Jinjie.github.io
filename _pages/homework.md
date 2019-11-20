---
layout: archive
title: "Assignments"
permalink: /Assignments/
author_profile: true
---

<!-- {% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %} -->
My experiment reports and assignments can be found 📄 here (for reports and assignments that have electronic versions).

{% include base_path %}

{% for post in site.Assignments reversed %}
  {% include archive-single.html %}
{% endfor %}