---
layout: page
title: Learning
permalink: /learning/
description: A collection of things I am currently learning, exploring, and experimenting with.
nav: true
nav_order: 4
horizontal: false
---

<div class="projects">

  <div class="row row-cols-1 row-cols-md-3">
    {% assign learning_projects = site.learning | sort: "importance" %}
    {% for project in learning_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>

</div>
