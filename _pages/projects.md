---
layout: page
title: Software
permalink: /software/
nav: true
nav_order: 5
horizontal: false
---

This page is intended as a brief showcase of some of the software projects I
have worked on that are not necessarily related to publications.
I only mention open-source projects available on GitHub - unfortunately none of
the `Go` projects I have collaborated on is publicly available.

<a href="https://github.com/cndolo">
  <img style="float: left" style ="padding: 0 1em 0 0;" src="https://github-readme-stats.vercel.app/api/?username=cndolo&show_icons=true&exclude_repo=cndolo.github.io"/>
</a>
<a href="https://github.com/cndolo">
  <img style="float: right" src="https://github-readme-stats.vercel.app/api/top-langs/?username=cndolo&layout=compact&exclude_repo=cndolo.github.io"/>
</a>
<br>
<br>

<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
