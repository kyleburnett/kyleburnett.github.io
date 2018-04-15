---
layout: default
title: "Recipes"
author: "Kyle Burnett"
permalink: /recipes/
---

<div class="catalogue compact">
    {% for recipe in site.recipes %}
        <a href="{{ recipe.url | prepend: site.baseurl }}" class="catalogue-item">
            <div>
                <h1 class="catalogue-title">{{ recipe.title }}</h1>
                <div class="catalogue-line"></div>
            </div>
        </a>
    {% endfor %}
</div>
