---
layout: page
title: projects
permalink: /projects/
description: A growing collection of my academic, creative, and collaborative work.
nav: true
nav_order: 3
horizontal: false
---

<div class="projects">

  <h2 class="category">Academic</h2>

  <div class="row row-cols-1 row-cols-md-3">
    {% assign academic_projects = site.projects | where: "category", "Academic" | sort: "importance" %}
    {% for project in academic_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>

  <h2 class="category">TEDx</h2>

  <div class="row row-cols-1 row-cols-md-3">
    {% assign tedx_projects = site.projects | where: "category", "TEDx" | sort: "importance" %}
    {% for project in tedx_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>

</div>
