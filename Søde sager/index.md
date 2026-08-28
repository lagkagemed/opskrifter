---
layout: default
---

{% assign current_path = page.path | split: "/" %}
{% assign current_folder = current_path[0] %}

### Files in {{ current_folder | replace: "-", " " | capitalize }}

<ul>
  <!-- Fyrst finna vit vanligar síður (t.d. .md fílur sum verða til HTML) -->
  {% for p in site.pages %}
    {% assign page_parts = p.path | split: "/" %}
    {% if page_parts[0] == current_folder %}
      {% assign page_name = page_parts | last %}
      {% unless page_name == "index.md" or page_name == "index.html" %}
        <li>
          <a href="{{ p.url | relative_url }}">{{ p.title | default: page_name }}</a>
        </li>
      {% endunless %}
    {% endif %}
  {% endfor %}
</ul>

[← Aftur til forsíðuna]({{ site.baseurl }}/)
