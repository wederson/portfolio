---
layout: page
title: Ordenados por Categorias
permalink: /categorias/
content-type: eg
---

<main>
    {%- for category in site.categories -%}
        <div class="pure-u-1 tags">
        <h2 id="{{ category | first }}">{{ category | first  }}</h2>
        {%- for post in category.last -%}
            <li id="category-content" style="padding-bottom: 0.6em;"><a href="{{post.url}}">{{ post.title }}</a></li>
        {%- endfor -%}
        </div>
    {%- endfor -%}
    <br/>
    <br/>
</main>
