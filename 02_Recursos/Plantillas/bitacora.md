<%*
// Obtener lista de integrantes de la carpeta 05_Integrantes
const integrantesFolder = app.vault.getAbstractFileByPath("05_Integrantes");
const integrantesFiles = integrantesFolder.children.filter(file => file.extension === "md" && file.name !== "example_user.md");

// Extraer nombres (quitando la extensión .md)
const nombresIntegrantes = integrantesFiles.map(file => file.basename);

// Crear opciones para el suggester
const opciones = nombresIntegrantes.length > 0 ? nombresIntegrantes : ["Armando Huitzilt Rodríguez", "Integrante Ejemplo"];

// Seleccionar integrante
const integranteSeleccionado = await tp.system.suggester(opciones, opciones, false, "Selecciona el integrante:");

// Crear versión sin espacios para el nombre del archivo
const integranteSinEspacios = integranteSeleccionado.replace(/\s+/g, "_").toLowerCase();

// Renombrar archivo
await tp.file.rename(tp.date.now("YYYY-MM-DD_HH-mm") + "_bitacora_" + integranteSinEspacios);
%>
# Bitácora Semanal - <% integranteSeleccionado %>

**Fecha:** <% tp.date.now("dddd, DD [de] MMMM [de] YYYY") %>
**Semana:** <% tp.date.now("YYYY-[W]WW") %>
**Integrante:** <% integranteSeleccionado %>

---

## 📋 Resumen de la Semana

### Objetivos Propuestos
- [ ] 
- [ ] 
- [ ] 

### Objetivos Cumplidos
- [x] 
- [x] 
- [x] 

---

## 🔧 Actividades Realizadas

### Lunes <% tp.date.now("DD/MM", -6) %>


### Martes <% tp.date.now("DD/MM", -5) %>


### Miércoles <% tp.date.now("DD/MM", -4) %>


### Jueves <% tp.date.now("DD/MM", -3) %>


### Viernes <% tp.date.now("DD/MM", -2) %>


### Sábado <% tp.date.now("DD/MM", -1) %>


### Domingo <% tp.date.now("DD/MM", 0) %>


---

## 📈 Progreso del Proyecto

### Logros Principales


### Dificultades Encontradas


### Soluciones Implementadas


---

## 📚 Aprendizajes

### Nuevos Conocimientos


### Habilidades Desarrolladas


### Recursos Útiles Descubiertos


---

## 🤝 Colaboración en Equipo

### Reuniones Asistidas


### Contribuciones al Equipo


### Feedback Recibido


---

## 📋 Pendientes para la Próxima Semana

### Tareas Prioritarias
- [ ] 
- [ ] 
- [ ] 

### Objetivos a Corto Plazo
- [ ] 
- [ ] 

### Recursos Necesarios


---

## 📝 Notas Adicionales

<% tp.file.cursor() %>

---

## 🔗 Enlaces Relevantes

- **Proyecto Principal:** [[]]
- **Reuniones Relacionadas:** [[]]
- **Referencias:** [[]]
- **Perfil del Integrante:** [[<% integranteSeleccionado %>]]

---

**Próxima Bitácora:** [[<% tp.date.now("YYYY-MM-DD", 7) %>_bitacora_<% integranteSinEspacios %>]]