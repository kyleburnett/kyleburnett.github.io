---
layout: default
title: "Collections"
author: "Kyle Burnett"
permalink: /collections/
---

## Algorithms

<div class="catalogue cozy">
    {% for post in site.algorithms_cormen %}
        <a href="{{ post.url | prepend: site.baseurl }}" class="catalogue-item">
            <div>
                <h1 class="catalogue-title">{{ post.title }}</h1>
                <time datetime="{{ post.date }}" class="catalogue-time">{{ post.date | date: "%B %d, %Y" }}</time>
                <div class="catalogue-line"></div>
            </div>
        </a>
    {% endfor %}
</div>
