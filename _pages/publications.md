---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

<!-- Group publications by the year extracted from pub_date -->
{% assign grouped_by_year = site.publications | group_by: "pub_date" %}

<!-- Extract the year from pub_date -->
{% assign grouped_by_year = grouped_by_year | map: "name" | map: "slice: 0, 4" %} <!-- Extract the year -->

{% for group in grouped_by_year reversed %}
  <h2>{{ group.name }}</h2> <!-- Display the year as a heading -->

  {% for post in group.items %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
