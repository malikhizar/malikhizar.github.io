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

{% assign grouped_posts = site.publications | group_by_exp:"post","post.date | date: '%Y'" %}

{% for group in grouped_posts %}
  <h2>{{ group.name }}</h2> <!-- This will display the year (group name) -->

  <ul class="publication-list">
    {% for post in group.items %}
      {% include archive-single.html %}
    {% endfor %}
  </ul>
{% endfor %}
