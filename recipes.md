---
layout: page
title: Recipes
permalink: /recipes/
---


  <ul class="post-list">
    {% for recipe in site.recipes %}
      <li>
        <span class="post-meta">{{ recipe.date | date: "%b %-d, %Y" }}</span>

        <h2>
          <a class="post-link" href="{{ recipe.url | prepend: site.baseurl }}">{{ recipe.title }}</a>
        </h2>
      </li>
    {% endfor %}
  </ul>


