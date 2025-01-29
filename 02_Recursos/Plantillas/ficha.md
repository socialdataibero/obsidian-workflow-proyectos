---
title: "[[<%* const Title = await tp.system.prompt('Ingrese el nombre de la Ficha:'); if (Title) { tp.file.rename(Title); tR += Title; } else { tR += 'Cambiar_manualmente'; } %>]]"
description: "<%* const desc = await tp.system.prompt('Ingrese una descripción breve de su ficha:'); tR += desc; %>"
category: []
status: En progreso🔵
tags:
  - Etiqueta1
  - Etiqueta2
priority: Baja🟢
creation_date: <% tp.file.creation_date("dddd Do MMMM YYYY HH:mm") %>
asigned_to:
  - "[[name1]]"
  - "[[name2]]"
---

---
> [!info]- ¿Cómo usar esta plantilla?
> 

---
## :RiBook2Fill: Control de metadatos

- **¡Controla el estatus y la prioridad de tu ficha dinámicamente!**

> [!state]- **Progreso:**
> ```meta-bind
> INPUT[select(option( Sin iniciar🔴), option(En progreso🔵), option(Completado🟢)):status]
> ```
 
> [!state]- **Prioridad:**
> ```meta-bind
> INPUT[select(option(Alta🔴), option(Media🔵), option(Baja🟢)):priority]
> ```

---
# :FasFilePen: Ficha técnica: `= this.title` 

---
## :RiProgress2Fill: Estado de compleción

> [!success]- **Secciones completadas**
> 1. [ ] Representación gráfica
> 2. [ ] Introducción
> 3. [ ] Explicación avanzada
> 4. [ ] Código de ejemplo
> 5. [ ] Tipos de datos aplicables
> 6. [ ] Supuestos de los datos
> 7. [ ] Ejemplos de aplicación práctica
> 8. [ ] Recursos adicionales
> 9. [ ] Referencias

---
## :LiGitGraph: Representación gráfica básica

> [!info]- **Instrucciones**
> Ingresa una imagen estilo ícono que represente de forma general el tema de tu ficha técnica.
> 
> No olvides citar la procedencia de tu imagen. Por defecto, los documentos (como imagenes) adjuntos se almacenan en la carpeta `04_Assets`. Organiza estos documentos de la mejor forma y dale un nombre adecuado a estos archivos. 

```markdown
![](ruta/relativa/de/la/imagen)
```

*Referencia*:

---
## :LiAlignStartHorizontal: Introducción

> [!info]- **Instrucciones**
> Haz una descripción general del tema de tu ficha. Puedes incluir los fundamentos, relevancia en el campo y características principales.
> 
> No olvides citar adecuadamente tus referencias.

---
## :LiExperiment: Explicación avanzada

> [!info]- **Instrucciones**
> Haz una descripción más avanzada del tema de tu ficha. Puedes hablar a profundidad de los fundamentos teóricos.
> 
> No olvides citar adecuadamente tus referencias.

### :RiAdvertisementFill: Representación gráfica avanzada

> [!info]- **Instrucciones**
> (*Opcional*) Agrega una imagen que complemente tu explicación.
> 
> No olvides referenciar la fuente.

```markdown
![](ruta/relativa/de/la/imagen)
```

---
## :LiCode2: Código de ejemplo

> [!info]- **Instrucciones**
> Proporciona un fragmento de código relacionado con el tema de tu ficha técnica. Es de utilidad generar un `notebook.ipynb` para describir a detalle aspectos del código (si aplica); en cuyo caso proporciona la ruta relativa el archivo.  

```code
// Ejemplo de código
```

```markdown
[](ruta/relativa/notebook)
```

---
## :RiDatabase2Fill: Tipos de datos

> [!info]- **Instrucciones**
> Enumera los tipos de datos que aplican en el contexto del tema.

---
## :LiDatabaseZap: Supuestos de los datos

> [!info]- **Instrucciones**
> Describe los supuestos o limitaciones de los datos relacionados con el tema.

---
## :LiChartNetwork: Ejemplos de aplicación práctica

> [!info]- **Instrucciones**
> Proporciona casos prácticos o ejemplos de cómo aplicar el tema en situaciones reales. Es de utilidad proporcionar links a proyectos en GitHub sobre estas aplicaciones. 

---
## :RiHeartAddFill: Recursos adicionales

> [!info]- **Instrucciones**
> Lista recursos adicionales útiles como enlaces, libros o artículos.

---
## :LiFileBox: Referencias

> [!info]- **Instrucciones**
> Proporciona las referencias usadas en esta ficha técnica. Consulta [¿Cómo citar?](07_docs/referencias) para mayor información.
