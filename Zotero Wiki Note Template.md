---
cssclasses:
  - infobox
cssclass: infobox
created in: '{{exportDate | format("YYYY-MM-DD")}}'
last updated: 2026-03-23
read status:
reason added:
alias: '{% if creators.length > 1 %}{{creators[0].lastName}} et al. {{date | format("YYYY")}}{% else %}{{creators[0].lastName}} {{date | format("YYYY")}}{% endif %}'
tags:
  - bibliographic-note
created: 2025-12-29
---
>[!infobox]+  
> [![Zotero Logo](zotero_logo.png)]({{url}})  
> ###### **Bibliography**  
>  |  |  
> ---|---|  
> Author(s): | {{authors}} |  
> Publication Date: | {{date | format("YYYY")}} |  
> Journal: | {{publicationTitle}} |  
> Volume: | {{volume}} |
> Issue: | {{issue}} |
> Page(s): | {{pages}}
> DOI: | {{DOI}}
> ###### **Additional Information**
>  | |
>  ---|---|
>  Added to Zotero: | {{dateAdded | format("YYYY-MM-DD HH:mm:ss")}}
>  Modified: | {{dateModified | format("YYYY-MM-DD HH:mm:ss")}}
>  Imported to Obsidian: | {{importDate | format("YYYY-MM-DD HH:mm:ss")}}
# {{title | escape}}
---
# Abstract
---
{{abstractNote}}
# Summary
---
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam tempor nunc sit amet nulla mollis, quis volutpat risus bibendum. Cras ligula justo, fermentum et magna et, feugiat blandit nisl. Donec ac quam massa. In eu luctus dolor. In in leo et ligula dignissim gravida. Morbi varius ipsum sem, dictum venenatis neque rhoncus eu. Ut dignissim consectetur risus ut iaculis. Phasellus tristique augue enim, vitae pretium augue mattis non. Phasellus orci quam, euismod sed ultricies ac, ullamcorper vel tellus. Fusce fermentum dignissim tincidunt. Quisque pretium tellus non sapien tempus, at cursus neque ornare. Vestibulum tempor eget orci malesuada ornare.
# Highlights & Comments
---
{% for annotation in annotations -%}
{%- if annotation.annotatedText -%} 
- [**"{{annotation.annotatedText | safe}}"**](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}})<br>
{%- if annotation.comment -%}  -- *{{annotation.comment|nl2br}}*{%- endif -%}
{% else %}
{{annotation.type | capitalize}}
{%- endif -%}
{%- if annotation.imageRelativePath %}
![[{{annotation.imageRelativePath}}]]
{%- endif %}
{% if annotation.allTags %}
{{annotation.allTags}}
{% endif %}
{% endfor -%}
# Citation
---
{{bibliography}}
# References
---
