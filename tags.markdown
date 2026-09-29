---
layout: page
title: Tags
permalink: /tags/
---
{%- assign names = "" | split: "" -%}
{%- for post in site.posts -%}
  {%- for name in post.tags -%}
    {%- unless names contains name -%}{%- assign names = names | push: name -%}{%- endunless -%}
  {%- endfor -%}
{%- endfor -%}
<ul class="category-list">
  {%- assign names = names | sort -%}
  {%- for name in names -%}
  {%- assign count = 0 -%}
  {%- for post in site.posts -%}{%- if post.tags contains name -%}{%- assign count = count | plus: 1 -%}{%- endif -%}{%- endfor %}
  <li>
    <a href="/tags/{{ name | slugify }}/">{{ name }}</a>
    <span class="post-meta">{{ count }} post{% if count != 1 %}s{% endif %}</span>
  </li>
  {%- endfor -%}
</ul>
