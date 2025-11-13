---
title: Demo Directory
layout: default
---

# 📁 Demo 目录

---

{% assign current_dir = page.path | replace: "index.md", "" %}
{% assign current_depth = current_dir | split: "/" | size %}

<ul>

{%- for file in site.static_files -%}
  {%- assign path = file.path -%}
  {%- assign name = path | split: "/" | last -%}
  {%- assign segments = path | split: "/" | size -%}

  {%- if path contains current_dir and
        segments == current_depth and
        name != "index.html" and
        name != "index.md" and
        path does not contain "/assets/" and
        path does not contain "/css/" and
        path does not contain "/scss/" and
        path does not contain "/styles/" -%}

    <li><a href="{{ file.path | relative_url }}">{{ name }}</a></li>

  {%- endif -%}
{%- endfor -%}

{%- for p in site.pages -%}
  {%- assign path = p.path -%}
  {%- assign name = path | split: "/" | last -%}
  {%- assign segments = path | split: "/" | size -%}

  {%- if path contains current_dir and
        segments == current_depth and
        name != "index.html" and
        name != "index.md" -%}

    <li><a href="{{ p.path | relative_url }}">{{ name }}</a></li>

  {%- endif -%}
{%- endfor -%}

</ul>
