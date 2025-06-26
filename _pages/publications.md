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

<!-- Print pub_date for all publications to debug -->
{% for post in site.publications %}
  <p>Publication Date: {{ post.pub_date }}</p>  <!-- Display the pub_date for each publication -->
{% endfor %}
