---

title: "{{title | replace('"',"'")}}"
{%- set camelRegex = r/([a-z])([A-Z])/g %}
{%- for type, creators in creators | groupby("creatorType") %} 
{% if creators.length > 1 %}{{type | replace(camelRegex, "$1 $2") | lower | trim}}s:{%- for creator in creators %}{% if creator.name %}
- {{creator.name}}{% else%}
- {{creator.firstName}} {{creator.lastName}} {% endif %}{%- endfor %} {% else -%}
{{type | replace(camelRegex, "$1-$2") | lower | trim}}:{%- for creator in creators %}{% if creator.name %} "{{creator.name}}"{% else%} "{{creator.firstName}} {{creator.lastName}}"{% endif -%}{%- endfor -%}{% endif -%}{% endfor %}
description: "<%* const desc = await tp.system.prompt('Ingrese un resumen breve del texto:'); tR += desc; %>"
category: []
year: {% if date %}{{date | format("YYYY")}}{% endif %}
status: "Por revisar🔴" 
priority: "Media🔵"
tags:
  - revisión-literatura
  - investigación
creation_date: <% tp.file.creation_date("dddd Do MMMM YYYY HH:mm") %>
temas_principales: "<%* const temas = await tp.system.prompt('Ingrese los temas principales:'); tR += temas; %>"
revisor: "<%*
const FOLDER = '05_Integrantes';              // carpeta en el root
const folder = app.vault.getAbstractFileByPath(FOLDER);
let opciones = [];

if (folder && folder.children) {
  // solo archivos .md directamente dentro de la carpeta (no recursivo)
  opciones = folder.children
    .filter(f => f.extension === 'md')
    .map(f => f.basename);
}

if (opciones.length === 0) {
  // fallback por si no hay notas o la carpeta no existe
  opciones = ['(No hay notas en 05_Integrantes)'];
}

const elegido = await tp.system.suggester(opciones, opciones, false, 'Selecciona revisor/a');
tR += elegido;
%>"

---

{%- set authorsList = [] -%}
{%- for c in creators -%}
    {%- if c.lastName -%}
        {%- set authorsList = authorsList.concat([c.lastName]) -%}
    {%- elif c.name -%}
        {%- set authorsList = authorsList.concat([c.name]) -%}
    {%- endif -%}
{%- endfor -%}

{# Crear la parte del autor de la cita #}
{%- set authorPart = "" -%}
{%- if authorsList.length > 2 -%}
    {%- set authorPart = authorsList[0] ~ " et al." -%}
{%- elif authorsList.length == 2 -%}
    {%- set authorPart = authorsList[0] ~ " & " ~ authorsList[1] -%}
{%- elif authorsList.length == 1 -%}
    {%- set authorPart = authorsList[0] -%}
{%- endif -%}

{# Extraer el año si la fecha existe #}
{%- set year = "" -%}
{%- if date -%}
    {%- set year = date | format("YYYY") -%}
{%- endif -%}

{# Unir todo en la cita final #}
{%- set apaCitation = authorPart -%}
{%- if authorPart and year -%}
    {%- set apaCitation = apaCitation ~ ", " ~ year -%}
{%- endif -%}

{{ "\n" }}


> [!info]- ¿Cómo usar esta plantilla?
> Esta plantilla está diseñada para sistematizar la revisión de literatura académica. Complete cada sección con la información relevante del texto analizado.
> Para mayor información, consulta [[ficha_revision_literatura_doc]]

---
## :RiBook2Fill: Control de avances

- **¡Controla el estatus y la relevancia de tu revisión dinámicamente!**

> [!state]- **Estado de revisión:**
> ```meta-bind
> INPUT[select(option(Por revisar🔴), option(En revisión🔵), option(Revisado🟢)):status]
> ```
 
> [!state]- **Relevancia para la investigación:**
> ```meta-bind
> INPUT[select(option(Alta🔴), option(Media🔵), option(Baja🟢)):priority]
> ```

---
# :FasFilePen: Ficha de revisión: {{ title }}

---
## :LiBookmark: Referencia bibliográfica

> [!warning]- **Advertencia**
> Se recomienda verificar la exactitud de esta cita, ya que ha sido generada a partir de la importación de metadatos.

### Cita APA 7 completa

```
{% for c in creators -%}
{%- if loop.first -%}
{%- if c.lastName -%}{{c.lastName}}, {{c.firstName | truncate(1, true, '') | upper}}.
{%- else -%}{{c.name}}{%- endif -%}
{%- elif loop.last and loop.index == 2 -%}
{%- if c.lastName -%}, & {{c.lastName}}, {{c.firstName | truncate(1, true, '') | upper}}.
{%- else -%}, & {{c.name}}{%- endif -%}
{%- elif loop.last -%}
{%- if c.lastName -%}, & {{c.lastName}}, {{c.firstName | truncate(1, true, '') | upper}}.
{%- else -%}, & {{c.name}}{%- endif -%}
{%- else -%}
{%- if c.lastName -%}, {{c.lastName}}, {{c.firstName | truncate(1, true, '') | upper}}.
{%- else -%}, {{c.name}}{%- endif -%}
{%- endif -%}
{%- endfor %} ({{year}}). {% if itemType == "bookSection" %}{{title}}. En {{bookTitle}}{% else %}{{title}}{% endif %}. {{publisher}}{% if DOI %}. https://doi.org/{{DOI}}{% endif %}
```

### Cita APA 7 en texto

```
({{ apaCitation }})
```

### Enlace a PDF en Zotero

- l! **Enlace en Zotero:** [Abrir en Zotero]({{desktopURI}})

---

## :LiInfo: Información básica del documento

{% if abstractNote %}
### Resumen original 

>[!abstract]- 
>{{ abstractNote }}
>{% endif %}

### Resumen personal:



### Palabras clave:
- 
- 
- 

### Tema(s) principal(es):
`= this.temas_principales`

### Tipo de texto:
{% if itemType %}
{{ itemType | default('-') }}
{% endif %}

### Idioma original:
{% if language %}
{{ language | default('-') }}
{% endif %}


---
## :LiTableOfContents: ¿Cuál es el contexto de la investigación?



---

## :FasFileInvoice: ¿Cuál es la brecha en la literatura? ¿Cuál es el motivo de la investigación?



---
## :LiHandHelping: ¿Cuál es la contribución? ¿De qué trata el artículo?

> ¿Cómo contribuye este artículo a nuestra comprensión de las cosas? 
> ¿Cómo arroja nueva luz? 
> ¿Qué tipo de contraargumento a la sabiduría convencional ofrece el autor?



---
## :LiDock: ¿Cuál es la conclusión de la investigación? 


---
## :LiQuote: Anotaciones (conceptos, metodología, descripción de datos, resultados etc.) 

> [!info]- **Instrucciones** 
> Utiliza Zotero para resaltar en color rosa las citas textuales más importantes de la referencia. Puedes agregar comentarios analíticos y etiquetas en cada fragmento resaltado.
> 
> > [!warning]+ ¡Atención! 
> > Asegúrate de que todas las citas estén resaltadas en color **ROSA** para poder ser importadas aquí.

> [!pink]- Citas textuales
> {% for annotation in annotations %}
> {% if annotation.color == "#e56eee" %}
> - _"{{ annotation.annotatedText }} {% if annotation.pageLabel %}"_ [({{ apaCitation }}, p. {{ annotation.pageLabel }})]({{ annotation.desktopURI }})
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
>   > **Comentarios**: {{ annotation.comment }}
>   {% endif %}
>
> {% endif %}
> {% endfor %}




---
## :LiPencil: Notas adicionales y reflexiones personales

### Reflexiones:


### Ideas para desarrollar:


---
## :LiFileBox: Enlaces y recursos complementarios

### Enlaces a recursos adicionales :
- 
- 

### Notas vinculadas:
- [[]]
- [[]]

---
## :LiCalendar: Metadatos de revisión

- **Fecha de última actualización:** <% tp.file.last_modified_date("dddd Do MMMM YYYY") %>
- **Revisor:** `= this.revisor`
- **Versión de la ficha:** 1.0