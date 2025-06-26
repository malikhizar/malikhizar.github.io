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

<!-- Group publications by year -->
{% assign publications_by_year = {} %}

<!-- Loop through all publications and group them by year -->
{% for post in site.publications %}
  {% assign year = post.pub_date | slice: 0, 4 %} <!-- Extract year from pub_date -->
  
  <!-- Print the year for debugging -->
  <p>Debug: {{ post.title }} - Year: {{ year }}</p>

  <!-- Initialize year group if not already done -->
  {% if publications_by_year[year] == nil %}
    {% assign publications_by_year[year] = "" %}
  {% endif %}
  
  <!-- Append the post to the respective year group -->
  {% assign publications_by_year[year] = publications_by_year[year] | append: post.url | append: "," %}
{% endfor %}

<!-- Make sure publications_by_year is not empty before sorting -->
{% if publications_by_year.size > 0 %}
  {% assign sorted_years = publications_by_year | keys | sort: "desc" %}
  
  {% for year in sorted_years %}
    <h2>{{ year }}</h2> <!-- Display the year as a heading -->
    <ul>
      {% assign post_urls = publications_by_year[year] | split: "," %}
      {% for post_url in post_urls %}
        {% assign post = site.publications | where: "url", post_url | first %}
        <li>
          <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.venue }}
        </li>
      {% endfor %}
    </ul>
  {% endfor %}
{% else %}
  <p>No publications found.</p> <!-- Handle the case where no publications are available -->
{% endif %}
