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

## Publications with current group (Gerstung Group @ EMBL-EBI)

{% for post in site.publications_current reversed %}
  {% include archive-single.html %}
{% endfor %}

## Publications with previous groups 

{% for post in site.publications_previous reversed %}
  {% include archive-single.html %}
{% endfor %}
