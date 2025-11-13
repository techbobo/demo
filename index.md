---
title: Demo Directory
layout: default
---

# 📁 Demo 目录

---

{% assign current_path = page.path | replace: "index.md", "" %}

<ul>
{% for file in site.static_files %}
  {% if file.path contains current_path %}
    {% assign name = file.path | split: "/" | last %}
    {% unless name == "index.md" or name == "index.html" %}
      <li>
        <a href="{{ file.path | relative_url }}">{{ name }}</a>
      </li>
    {% endunless %}
  {% endif %}
{% endfor %}

{% for p in site.pages %}
  {% if p.path contains current_path %}
    {% assign name = p.path | split: "/" | last %}
    {% unless name == "index.md" or name == "index.html" %}
      <li>
        <a href="{{ p.path | relative_url }}">{{ name }}</a>
      </li>
    {% endunless %}
  {% endif %}
{% endfor %}
</ul>
