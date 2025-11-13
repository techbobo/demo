---
layout: default
title: Demo 文件目录
---

# 📁 Demo 目录

---

{% assign folder = "/demo/" %}

{% comment %}
列出所有静态文件（图片、JS、CSS 等）
{% endcomment %}
{% assign static_files = site.static_files | where_exp:"file","file.path contains folder" %}

{% comment %}
列出所有页面（HTML）
{% endcomment %}
{% assign pages = site.pages | where_exp:"p","p.path contains folder" %}

{% assign all = static_files | concat: pages %}

{% if all.size == 0 %}
暂无文件
{% else %}

<ul>
{% for item in all %}
  {% assign name = item.path | split:"/" | last %}
  {% if name != "index.md" and name != "index.html" %}
  <li>
     <a href="{{ item.path | relative_url }}">
       {{ name }}
     </a>
  </li>
  {% endif %}
{% endfor %}
</ul>

{% endif %}
