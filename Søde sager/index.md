---
layout: default
---

{% assign current_path = page.path | split: "/" %}
{% assign current_folder = current_path[0] %}

### Files in {{ current_folder | replace: "-", " " | capitalize }}

<ul>
  {% for file in site.static_files %}
    {% assign file_parts = file.path | split: "/" %}
    {% if file_parts[1] == current_folder %}
      {% assign file_name = file_parts | last %}
      {% unless file_name == "index.md" or file_name == "index.html" %}
        <li>
          <a href="{{ site.baseurl }}{{ file.path }}">{{ file_name }}</a>
        </li>
      {% endunless %}
    {% endif %}
  {% endfor %}
</ul>

[← Aftur til forsíðuna]({{ site.baseurl }}/)
