---
title: Demo 目录
layout: default
---

# 📁 Demo 目录

---

<ul>

{%- for file in site.static_files -%}
  {%- assign path = file.path -%}
  {%- assign name = file.path | split:"/" | last -%}

  {%- if path != "/index.html"
        and name != "index.md"
        and path does not contain "/assets/"
        and path does not contain "/css/"
        and path does not contain "/scss/"
        and path does not contain "/styles/" -%}

      <li><a href="{{ file.path | relative_url }}">{{ name }}</a></li>

  {%- endif -%}

{%- endfor -%}


{%- for p in site.pages -%}
  {%- assign path = p.path -%}
  {%- assign name = p.path | split:"/" | last -%}

  {%- if name != "index.html" and name != "index.md" -%}
      <li><a href="{{ p.path | relative_url }}">{{ name }}</a></li>
  {%- endif -%}

{%- endfor -%}

</ul>
