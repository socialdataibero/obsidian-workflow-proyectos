---
citekey: {{citekey}}
aliases:
- "{%- if creators -%}
        {{creators[0].lastName or creators[0].name }}
        {%- if creators|length == 2 %} & {{creators[1].lastName or creators[1].name}}{% endif -%}
        {%- if creators|length > 2 %} et al.{% endif -%}
    {%- endif -%}
    {%- if date %} ({{date | format("YYYY")}}){% endif -%} 
    {%- if shortTitle %} {{shortTitle | safe}} {%- else %} {{title | safe}} {%- endif -%}"{% if itemType == "bookSection" %}
book-title: "{{bookTitle | replace('"',"'")}}"{% endif %}
title: "{{title | replace('"',"'")}}"
{%- set camelRegex = r/([a-z])([A-Z])/g %}
{%- for type, creators in creators | groupby("creatorType") %} 
{% if creators.length > 1 %}{{type | replace(camelRegex, "$1 $2") | lower | trim}}s:{%- for creator in creators %}{% if creator.name %}
- {{creator.name}}{% else%}
- {{creator.firstName}} {{creator.lastName}} {% endif %}{%- endfor %} {% else -%}
{{type | replace(camelRegex, "$1-$2") | lower | trim}}:{%- for creator in creators %}{% if creator.name %} "{{creator.name}}"{% else%} "{{creator.firstName}} {{creator.lastName}}"{% endif -%}{%- endfor -%}{% endif -%}{% endfor %}
year: {% if date %}{{date | format("YYYY")}}{% endif %}
item-type: {{itemType | replace(camelRegex, "$1 $2") | title | trim}}
publisher: {% if publicationTitle %}"{{publicationTitle}}"{% else %}"{{publisher}}"{% endif %}
{%- if notes.length > 0 -%}
{%- set longShortCutoff = 20 -%}
{%- set shortnotes = [] -%}
{%- set longnotes = [] -%}
{%- for note in notes -%}
{%- if note.note | wordcount <= longShortCutoff -%}
{%- set shortnotes = (shortnotes.push(note.note), shortnotes) -%} 
{%- else -%}
{%- set longnotes = (longnotes.push(note), longnotes) -%}
{%- endif -%}{%- endfor -%}{%- endif -%}
{%- for comment in shortnotes %}
{%- if comment and loop.first %}
comments:
{% endif -%}
- "{{comment|replace('"',"'")| replace("\n"," ")}}"{% endfor %}
tags:{% for t in tags %}
- {{t.tag | replace(r/\s+/g, "-")}}{% endfor %}{% if DOI %}
doi: https://doi.org/{{DOI}}{% endif %}{% if itemType == "book" %}
ISBN: {{ISBN}}{% endif %}
cssclasses: 
- literature-note{% if attachments.length > 0 %}{% for attachment in attachments %}{% if loop.first %}
attachments:{% endif %}
- {{attachment.path}}{% endfor %}{% endif %}
libraryID: {{libraryID}}
status: 
priority:
asigned: [[example_user]]
---

<!-- NO MODIFIQUES ESTA PLANTILLA A MENOS QUE SEAS EL ADMINISTARDOR -->

---
{%- set authorsList = [] -%}
{%- for c in creators -%}
    {%- if c.lastName -%}
        {%- set authorsList = authorsList.concat([c.lastName]) -%}
    {%- elif c.name -%}
        {%- set authorsList = authorsList.concat([c.name]) -%}
    {%- endif -%}
{%- endfor -%}

{# Definir el primer autor con una comprobación if-else #}
{%- if authorsList.length > 0 -%}
    {%- set firstAuthor = authorsList[0] -%}
{%- else -%}
    {%- set firstAuthor = "" -%}
{%- endif -%}

{# Definir el año a partir de la fecha, si está disponible #}
{%- if date -%}
    {%- set year = date | format("YYYY") -%}
{%- else -%}
    {%- set year = "" -%}
{%- endif -%}

{# Construir la cita en formato APA según el número de autores #}
{%- if authorsList.length > 2 -%}
    {%- set apaCitation = firstAuthor ~ " et al. " ~ year ~ " " -%}
{%- elif authorsList.length == 2 -%}
    {%- set apaCitation = authorsList[0] ~ " & " ~ authorsList[1] ~ " " ~ year ~ "" -%}
{%- elif authorsList.length == 1 -%}
    {%- set apaCitation = firstAuthor ~ " " ~ year ~ "" -%}
{%- else -%}
    {%- set apaCitation = "" -%}
{%- endif -%}

---

`BUTTON[actualizar-nota-literatura]` `INPUT[inlineSelect(option(No iniciado🔴), option(En progreso🔵), option(Terminado🟢)):status]` `INPUT[inlineSelect(option(Alta🔴), option(Media🔵), option(Baja🟢)):priority]`
  
---
# :LiNewspaper: {{ title }}

- n! **Autores**:  {{ authors }}
- ava! **Año**: {{ date | format('YYYY') }}
- z! **Cita:** {{ citekey }}

- l! **Enlace en Zotero:** [Abrir en Zotero]({{desktopURI}})


## :RiColorFilterFill: Anotaciones clasificadas por color

> [!yellow]- Amarillo
> {% for annotation in annotations %}
> {% if annotation.color == "#ffd400" %}
> - {{ annotation.annotatedText }} {% if annotation.pageLabel %} [({{ apaCitation }}, p. {{ annotation.pageLabel }})]({{ annotation.desktopURI }}){% endif %}
>   
>   {% if annotation.tags and annotation.tags.length > 0 %}
>   > **Tags**:
>   {% for t in annotation.tags %}
>   #{{ t.tag | replace(r/\s+/g,"-") }}{% if not loop.last %}, {% endif %}
>   {% endfor %}
>   {% endif %}
>
>   {% if annotation.comment %}
>   > **Nota**: {{ annotation.comment }}
>   {% endif %}
>
> {% endif %}
> {% endfor %}

> [!blue]- Azul
> {% for annotation in annotations %}
> {% if annotation.color == "#2ea8e5" %}
> - {{ annotation.annotatedText }}{% if annotation.pageLabel %}[({{ apaCitation }}, p. {{ annotation.pageLabel }})]({{ annotation.desktopURI }})
>   {% endif %}
>   
>   {% if annotation.tags and annotation.tags.length > 0 %}
>   > **Tags**:
>   {% for t in annotation.tags %}
>   #{{ t.tag | replace(r/\s+/g,"-") }}{% if not loop.last %}, {% endif %}
>   {% endfor %}
>   {% endif %}
>
>   {% if annotation.comment %}
>   > **Nota**: {{ annotation.comment }}
>   {% endif %}
>
> {% endif %}
> {% endfor %}

> [!green]- Verde
> {% for annotation in annotations %}
> {% if annotation.color == "#5fb236" %}
> - {{ annotation.annotatedText }}{% if annotation.pageLabel %} [({{ apaCitation }}, p. {{ annotation.pageLabel }})]({{ annotation.desktopURI }})
>   {% endif %}
>   
>   {% if annotation.tags and annotation.tags.length > 0 %}
>   > **Tags**:
>   {% for t in annotation.tags %}
>   #{{ t.tag | replace(r/\s+/g,"-") }}{% if not loop.last %}, {% endif %}
>   {% endfor %}
>   {% endif %}
>
>   {% if annotation.comment %}
>   > **Nota**: {{ annotation.comment }}
>   {% endif %}
>
> {% endif %}
> {% endfor %}

> [!red]- Rojo
> {% for annotation in annotations %}
> {% if annotation.color == "#ff6666" %}
> - {{ annotation.annotatedText }} {% if annotation.pageLabel %} [({{ apaCitation }}, p. {{ annotation.pageLabel }})]({{ annotation.desktopURI }})
>   {% endif %}
>   
>   {% if annotation.tags and annotation.tags.length > 0 %}
>   > **Tags**:
>   {% for t in annotation.tags %}
>   #{{ t.tag | replace(r/\s+/g,"-") }}{% if not loop.last %}, {% endif %}
>   {% endfor %}
>   {% endif %}
>
>   {% if annotation.comment %}
>   > **Nota**: {{ annotation.comment }}
>   {% endif %}
>
> {% endif %}
> {% endfor %}

> [!purple]- Morado
> {% for annotation in annotations %}
> {% if annotation.color == "#a28ae5" %}
> - {{ annotation.annotatedText }} {% if annotation.pageLabel %} [({{ apaCitation }}, p. {{ annotation.pageLabel }})]({{ annotation.desktopURI }})
>   {% endif %}
>   
>   {% if annotation.tags and annotation.tags.length > 0 %}
>   > **Tags**:
>   {% for t in annotation.tags %}
>   #{{ t.tag | replace(r/\s+/g,"-") }}{% if not loop.last %}, {% endif %}
>   {% endfor %}
>   {% endif %}
>
>   {% if annotation.comment %}
>   > **Nota**: {{ annotation.comment }}
>   {% endif %}
>
> {% endif %}
> {% endfor %}

> [!pink]- Rosa
> {% for annotation in annotations %}
> {% if annotation.color == "#e56eee" %}
> - {{ annotation.annotatedText }} {% if annotation.pageLabel %} [({{ apaCitation }}, p. {{ annotation.pageLabel }})]({{ annotation.desktopURI }})
>   {% endif %}
>   
>   {% if annotation.tags and annotation.tags.length > 0 %}
>   > **Tags**:
>   {% for t in annotation.tags %}
>   #{{ t.tag | replace(r/\s+/g,"-") }}{% if not loop.last %}, {% endif %}
>   {% endfor %}
>   {% endif %}
>
>   {% if annotation.comment %}
>   > **Nota**: {{ annotation.comment }}
>   {% endif %}
>
> {% endif %}
> {% endfor %}

> [!orange]- Naranja
> {% for annotation in annotations %}
> {% if annotation.color == "#f19837" %}
> - {{ annotation.annotatedText }} {% if annotation.pageLabel %} [({{ apaCitation }}, p. {{ annotation.pageLabel }})]({{ annotation.desktopURI }})
>   {% endif %}
>   
>   {% if annotation.tags and annotation.tags.length > 0 %}
>   > **Tags**:
>   {% for t in annotation.tags %}
>   #{{ t.tag | replace(r/\s+/g,"-") }}{% if not loop.last %}, {% endif %}
>   {% endfor %}
>   {% endif %}
>
>   {% if annotation.comment %}
>   > **Nota**: {{ annotation.comment }}
>   {% endif %}
>
> {% endif %}
> {% endfor %}

> [!gray]- Gris
> {% for annotation in annotations %}
> {% if annotation.color == "#aaaaaa" %}
> - {{ annotation.annotatedText }} {% if annotation.pageLabel %} [({{ apaCitation }}, p. {{ annotation.pageLabel }})]({{ annotation.desktopURI }})
>   {% endif %}
>   
>   {% if annotation.tags and annotation.tags.length > 0 %}
>   > **Tags**:
>   {% for t in annotation.tags %}
>   #{{ t.tag | replace(r/\s+/g,"-") }}{% if not loop.last %}, {% endif %}
>   {% endfor %}
>   {% endif %}
>
>   {% if annotation.comment %}
>   > **Nota**: {{ annotation.comment }}
>   {% endif %}
>
> {% endif %}
> {% endfor %}