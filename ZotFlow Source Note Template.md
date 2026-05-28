---
citationKey: {{ item.citationKey | json }}
aliases:
  - "{% if item.creators.size > 2 %}{{ item.creators.first.name | split: ' ' | last }} et al. ({{ item.date | slice: 0, 4 }}){% elsif item.creators.size == 2 %}{{ item.creators[0].name | split: ' ' | last }} & {{ item.creators[1].name | split: ' ' | last }} ({{ item.date | slice: 0, 4 }}){% else %}{{ item.creators.first.name | split: ' ' | last }} ({{ item.date | slice: 0, 4 }}){% endif %}"
  - "{% if item.creators.size > 2 %}{{ item.creators.first.name | split: ' ' | last }} et al. {{ item.date | slice: 0, 4 }}{% elsif item.creators.size == 2 %}{{ item.creators[0].name | split: ' ' | last }} & {{ item.creators[1].name | split: ' ' | last }} {{ item.date | slice: 0, 4 }}{% else %}{{ item.creators.first.name | split: ' ' | last }} {{ item.date | slice: 0, 4 }}{% endif %}"
itemType: {{ item.itemType | json }}
publication: {{ item.publicationTitle | default: item.publisher | replace: '&amp;', '&' | json }}
year: {{ item.date | slice: 0, 4 }}
cssClass: infobox
reasonAdded:
readStatus:
reviewStatus:
---

>[!infobox]+  
> {%- for attachment in item.attachments -%}{%- for annotation in attachment.annotations -%}{%- if annotation.type == "image" -%}[![[Attachments/{{ annotation.key }}.png]]]({{ item.url }}){%- break -%}{%- endif -%}{%- endfor -%}{%- endfor -%}

> ###### **Bibliography**
> **Author(s):** {% assign total = item.creators.size %}{% for c in item.creators %}{% if forloop.index <= 3 %}{{ c.name }}{% unless forloop.index == 3 or forloop.last %}; {% endunless %}{% endif %}{% endfor %}{% if total > 3 %} et al.{% endif %}
> **Publication Date:** {{ item.date }}
> **Journal:** {{ item.publicationTitle | default: item.publisher }}
> **Volume:** {{ item.volume }}
> **Issue:** {{ item.issue }}
> **Page(s):** {{ item.pages }}
> **DOI:** {{ item.DOI }}
> ###### **Additional Information**
> **Added to Zotero:** {{ item.dateAdded | date: '%Y-%m-%d %H:%M:%S' }}
> **Modified:** {{ item.dateModified | date: '%Y-%m-%d %H:%M:%S' }}
> **URL:** {{ item.url }}

# {{ item.title | striptags | escape }}
---
{%- if item.abstractNote -%}
# Abstract
---
{{ item.abstractNote | replace: newline, quote_string }}

{%- endif -%}
{%- if item.attachments.length > 0 -%}
# Attachments
---
{%- for attachment in item.attachments -%}
- [{{ attachment.filename }}](obsidian://zotflow?type=open-attachment&libraryID={{ attachment.libraryID }}&key={{ attachment.key }})
{%- endfor -%}
{%- endif -%}
{%- if item.attachments.length > 0 and item.attachmentAnnotations.length > 0 -%}
# Annotations
---
{%- assign firstImageSkipped = false -%}
{%- for attachment in item.attachments -%}
{%- if attachment.annotations.length > 0 -%}
{%- for annotation in attachment.annotations -%}
{%- if annotation.type == "ink" or annotation.type == "image"-%}
{%- if firstImageSkipped == false -%}
{%- assign firstImageSkipped = true -%}
{%- else -%}
![[{{settings.annotationImageFolder}}/{{ annotation.key }}.png]]
{%- endif -%}
{%- else -%}
>[!cite] %%empty%%
>*{{ annotation.text | replace: newline, quote_string_2 }}* [p.{{ annotation.pageLabel }}](obsidian://zotflow?type=open-attachment&libraryID={{ attachment.libraryID }}&key={{ attachment.key }}&navigation={{ annotation.key | process_nav_info}})
>→{{ annotation.comment | replace: newline, quote_string }}

{%- endif -%}
{%- endfor -%}
{%- endif -%}
{%- endfor -%}
{%- endif -%}