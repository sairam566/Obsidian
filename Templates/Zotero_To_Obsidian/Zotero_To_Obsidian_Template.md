
### Title:: {{title}}
- `Language:` {{language}}
- `Authors:` {{authors}}
- `Added Date:` {{dateAdded | format("YYYY-MM-DD h:mm a")}}
### Imported: {{importDate | format("YYYY-MM-DD h:mm a")}}
- `PDF Location:` {{pdfLink}}
- `Zotero Link:` {{pdfZoteroLink}}

{% for annotation in annotations -%}
{%- if annotation.annotatedText -%} - "{{annotation.annotatedText}}" {% if annotation.color %} {{annotation.colorCategory}} {{annotation.type | capitalize}} {% else %} {{annotation.type | capitalize}} {% endif %} [Page {{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}}) 
{% endif %}

{% if annotation.imageRelativePath -%} 
  ![[{{annotation.imageRelativePath}}]]{% endif %}
{% if annotation.comment %}
```
 {{annotation.comment}} 
``` 
{% endif %}
{% endfor -%}