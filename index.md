---
layout: default
title: Top page
---

<div class="project-grid">
  {% for project in site.projects %}
    <div class="project-item">
      <a href="{{ site.baseurl }}{{ project.url }}">
        <p>{{ project.title }}</p>
      </a>
    </div>
  {% endfor %}
</div>
