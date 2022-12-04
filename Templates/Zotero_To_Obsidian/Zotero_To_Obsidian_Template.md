
- `Title:` {{title}}
- `Language:` {{language}}
- `Authors:` {{authors}}
- `ISBN:` {{ISBN}}
- `Pages:` {{numPages}}
- `Tags:` {% for t in tags %}{{t.tag}}{% if not loop.last %}, {% endif %}{% endfor %}
- `Added Date:` {{dateAdded | format("YYYY-MM-DD h:mm a")}}
- `Imported:` {{importDate | format("YYYY-MM-DD h:mm a")}}
- `PDF Location:` {{pdfLink}}
- `Zotero Link:` {{pdfZoteroLink}}

%%
	Each time you import data from the same Zotero entry, it will overwrite the existing markdown file. You can prevent this using the `persist` template tag.
	Ref: %https://github.com/mgmeyers/obsidian-zotero-integration/blob/main/docs/Templating.md
%%
## My take on this book:
{% persist "notes" %}

{% endpersist %}

## Summary of key points:

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