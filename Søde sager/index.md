---

## layout: default

{% assign current_path = page.path | split: "/" %}
{% assign current_folder = current_path[0] %}

### Files in {{ current_folder | replace: "-", " " | capitalize }}

<ul>
  {% for p in site.pages %}
    {% assign page_parts = p.path | split: "/" %}
    {% assign page_name = page_parts | last %}

```
{% if page_parts[0] == current_folder and page_name contains ".md" %}
  {% unless page_name == "index.md" %}
    {% assign display_name = page_name | remove: ".md" | replace: "-", " " | capitalize %}
    <li>
      <a href="{{ p.url | relative_url }}">{{ p.title | default: display_name }}</a>
    </li>
  {% endunless %}
{% endif %}
```

{% endfor %}

</ul>

[← Aftur til forsíðuna]({{ site.baseurl }}/)
