---
title: Home
---

### Project Folders

<ul>
  {% assign listed_folders = "" | split: "," %}
  {% for file in site.static_files %}
    {% assign parts = file.path | split: "/" %}
    {% if parts.size > 2 %}
      {% assign folder_name = parts[1] %}
      {% unless listed_folders contains folder_name or folder_name.size == 0 or folder_name contains "_" or folder_name == "assets" %}
        <li>
          <a href="{{ site.baseurl }}/{{ folder_name }}/">{{ folder_name | replace: "-", " " | capitalize }}</a>
        </li>
        {% assign listed_folders = listed_folders | push: folder_name %}
      {% endunless %}
    {% endif %}
  {% endfor %}
</ul>
