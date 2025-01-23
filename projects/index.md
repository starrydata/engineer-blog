---
layout: default
title: Top page
---

# プロジェクト一覧

<div class="project-grid">
  {% for project in site.projects %}
    <div class="project-item">
      <a href="{{ project.url }}">
        <h2>{{ project.title }}</h2>
      </a>
    </div>
  {% endfor %}
</div>
