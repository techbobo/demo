---
title: Demo Directory
layout: default
---

# 📁 Demo 目录

---

{% assign current_dir = page.path | replace: "index.md", "" %}

<ul>

{%- comment -%}
列出当前目录中的 HTML/JS/CSS/图片等真实文件
排除 Jekyll 主题生成的文件（比如 /assets/css/style.scss）
{%- endcomment -%}

{%- for file in site.static_files -%}
  {%- assign path = file.path -%}
  {%- assign name = path | split: "/" | last -%}

  {%- if path startswith current_dir and
        name != "index.html" and
        name != "index.md" and
        path does not contain "/assets/" and
        path does not contain "/css/" and
        path does not contain "/scss/" and
        path does not contain "/styles/"
    -%}

    <li><a href="{{ file.path | relative_url }}">{{ name }}</a></li>

  {%- endif -%}
{%- endfor -%}


{%- comment -%}
列出当前目录中的 HTML 页面
{%- endcomment -%}

{%- for p in site.pages -%}
  {%- assign path = p.path -%}
  {%- assign name = path | split: "/" | last -%}

  {%- if path startswith current_dir and
        name != "index.html" and
        name != "index.md"
    -%}

    <li><a href="{{ p.path | relative_url }}">{{ name }}</a></li>

  {%- endif -%}
{%- endfor -%}

</ul>
