---
title: "[[<%* const Title = await tp.system.prompt('Ingrese el título del artículo/texto:'); if (Title) { tp.file.rename(Title); tR += Title; } else { tR += 'Cambiar_manualmente'; } %>]]"
description: "<%* const desc = await tp.system.prompt('Ingrese un resumen breve del texto:'); tR += desc; %>"
category: []
status: Por revisar🔴
tags:
  - revisión-literatura
  - investigación
priority: Media🔵
creation_date: <% tp.file.creation_date("dddd Do MMMM YYYY HH:mm") %>
area_disciplinar: "<%* const area = await tp.system.prompt('Ingrese el área disciplinar:'); tR += area; %>"
tipo_texto: "<%* const tipo = await tp.system.prompt('Tipo de texto (artículo, tesis, libro, etc.):'); tR += tipo; %>"
---

---
> [!info]- ¿Cómo usar esta plantilla?
> Esta plantilla está diseñada para sistematizar la revisión de literatura académica. Complete cada sección con la información relevante del texto analizado.

---
## :RiBook2Fill: Control de metadatos

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
# :FasFilePen: Ficha de revisión: `= this.title` 

---
## :RiProgress2Fill: Estado de compleción

> [!success]- **Secciones completadas**
> 1. [ ] Referencia bibliográfica
> 2. [ ] Resumen del texto
> 3. [ ] Información básica
> 4. [ ] Planteamiento central
> 5. [ ] Objetivos y preguntas
> 6. [ ] Marco conceptual
> 7. [ ] Autores citados
> 8. [ ] Conclusiones
> 9. [ ] Relación con la investigación
> 10. [ ] Análisis contextual
> 11. [ ] Citas relevantes

---
## :LiBookmark: Referencia bibliográfica

> [!info]- **Instrucciones**
> Ingrese la referencia completa en formato APA 7 o el formato requerido por su institución.

```markdown
Autor(es). (Año). Título del trabajo. Editorial/Revista.
```

---
## :LiFileText: Resumen del texto

> [!info]- **Instrucciones**
> Proporcione un resumen ejecutivo de 200-300 palabras sobre qué aborda el texto principal.

### Resumen general:

### Palabras clave:
- 
- 
- 

---
## :LiInfo: Información básica del documento

### Área disciplinar:
`= this.area_disciplinar`

### Tipo de texto:
`= this.tipo_texto`

### Año de publicación:

### Idioma original:

### Extensión (páginas):

---
## :LiTarget: Planteamiento central del texto

> [!info]- **Instrucciones**
> Describa la tesis principal o argumento central que desarrolla el autor/a.

### Tesis principal:

### Problema de investigación:

### Hipótesis (si aplica):

---
## :LiSearch: Objetivos y/o preguntas de investigación

> [!info]- **Instrucciones**
> Liste los objetivos principales y las preguntas de investigación que guían el texto.

### Objetivo general:

### Objetivos específicos:
1. 
2. 
3. 

### Preguntas de investigación:
1. 
2. 
3. 

---
## :LiNetwork: Categorías y/o conceptos centrales

> [!info]- **Instrucciones**
> Identifique y defina los conceptos clave que estructuran el texto.

### Conceptos principales:

| Concepto | Definición según el autor/a | Página |
|----------|----------------------------|---------|
|          |                            |         |
|          |                            |         |
|          |                            |         |

### Categorías de análisis:
- 
- 
- 

---
## :LiUsers: Autores/as que retoma para hablar del tema central

> [!info]- **Instrucciones**
> Liste los autores principales citados y cómo contribuyen al argumento.

### Autores fundamentales:

| Autor/a | Obra citada | Aporte al argumento | Página |
|---------|-------------|-------------------|---------|
|         |             |                   |         |
|         |             |                   |         |
|         |             |                   |         |

### Corrientes teóricas identificadas:
- 
- 

---
## :LiCheckSquare: Conclusiones y/o resultados de la investigación

> [!info]- **Instrucciones**
> Sintetice las conclusiones principales y hallazgos del texto.

### Conclusiones principales:
1. 
2. 
3. 

### Hallazgos relevantes:
- 
- 
- 

### Limitaciones reconocidas:
- 
- 

### Recomendaciones del autor/a:
- 
- 

---
## :LiLink: Relación del artículo con el tema general de la investigación

> [!info]- **Instrucciones**
> Explique cómo este texto se relaciona con su investigación actual.

### Relevancia para mi investigación:

### Aportes específicos:
- 
- 
- 

### Vacíos que ayuda a llenar:
- 
- 

### Nuevas preguntas que genera:
- 
- 

---
## :LiMessageSquare: Preguntas y comentarios al texto

### ¿En qué contexto se sitúa el texto?

> [!info]- **Instrucciones**
> Describa el contexto histórico, geográfico, político o académico del texto.

#### Contexto histórico:

#### Contexto geográfico:

#### Contexto académico/institucional:

### ¿Cómo define los conceptos centrales?

> [!info]- **Instrucciones**
> Analice el enfoque teórico y metodológico para definir conceptos.

#### Enfoque teórico:

#### Metodología utilizada:

#### Originalidad en las definiciones:

---
## :LiQuote: Citas textuales comentadas

> [!info]- **Instrucciones**
> Incluya las citas más relevantes con su respectivo comentario analítico.

### Cita 1:
> "[Insertar cita textual]" (p. XX)

**Comentario:**

### Cita 2:
> "[Insertar cita textual]" (p. XX)

**Comentario:**

### Cita 3:
> "[Insertar cita textual]" (p. XX)

**Comentario:**

---
## :LiPencil: Notas adicionales y reflexiones personales

> [!info]- **Instrucciones**
> Espacio libre para reflexiones, ideas emergentes o conexiones con otros textos.

### Reflexiones:

### Ideas para desarrollar:

### Conexiones con otros textos:
- [[Texto relacionado 1]]
- [[Texto relacionado 2]]

---
## :LiFileBox: Enlaces y recursos complementarios

> [!info]- **Instrucciones**
> Agregue enlaces a recursos relacionados, PDFs, o notas adicionales.

### Archivo PDF original:
```markdown
[](ruta/relativa/al/PDF)
```

### Enlaces relacionados:
- 
- 

### Notas vinculadas:
- [[]]
- [[]]

---
## :LiCalendar: Metadatos de revisión

- **Fecha de lectura:** 
- **Tiempo dedicado:** 
- **Fecha de última actualización:** <% tp.file.last_modified_date("dddd Do MMMM YYYY") %>
- **Revisor:** 
- **Versión de la ficha:** 1.0