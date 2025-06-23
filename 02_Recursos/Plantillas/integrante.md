---
full_name: "[[<%* const fullName = await tp.system.prompt('Ingrese su nombre completo:'); tp.file.rename(fullName); tR += fullName; %>]]"
phone: "<%* const phone = await tp.system.prompt('Ingrese su número de teléfono (Ej. 55 56 57 58):'); tR += phone; %>"
github: "<%* const defaultGithub = 'github_example_user'; const github = await tp.system.prompt('Ingrese su nombre de usuario en GitHub:', defaultGithub); tR += github; %>"
zotero: "<%* const defaultZotero = 'zotero_example_user'; const zotero = await tp.system.prompt('Ingrese su nombre de usuario en Zotero:', defaultZotero); tR += zotero; %>"
mattermost: "<%* const defaultMattermost = '@mattermost_example_user'; const mattermost = await tp.system.prompt('Ingrese su nombre de usuario en Mattermost:', defaultMattermost); tR += mattermost; %>"
email: "<%* const email = await tp.system.prompt('Ingrese su correo electrónico (Ej. john_doe@example.com):'); tR += email; %>"
availability: "<%* const defaultAvailability = 'Lunes a Viernes de 9:00 am - 6:00 pm'; const availability = await tp.system.prompt('Ingrese su disponibilidad de horario:', defaultAvailability); tR += availability; %>"
role: "<%* const defaultRole = 'Investigador y desarrollador python'; const role = await tp.system.prompt('Ingrese su rol dentro del proyecto:', defaultRole); tR += role; %>"
creation_date: "<% tp.file.creation_date('dddd Do MMMM YYYY HH:mm') %>"
---

---
> [!info]- ¡Lee antes de continuar!  
> - La información que completes en el `frontmatter` (Tablero de propiedades) se mostrará automáticamente más abajo en la nota.
> - Si necesitas hacer cambios, edítalos directamente en el `frontmatter`.
> - Los cambios no siempre se aplican de inmediato. Es posible que debas cerrar y volver a abrir la nota para verlos reflejados.
> - No completes la sección _[[#¡Queremos conocerte mejor!]]_ en el `frontmatter`. Este espacio es libre y puedes llenarlo como prefieras.

---
# :LiCircleUser: **Perfil del integrante**: `= this.full_name` 

--- 
## Información personal 

- n!  Nombre: `= this.full_name` 
- p!  Teléfono: `= this.phone`
- e!  Correo electrónico: `= this.email`

---
## Usuario en plataformas

- g! GitHub: `= this.github`
- z! Zotero: `= this.zotero`
- m! Mattermost: `= this.mattermost` 

---
## Información profesional 

- ava! Disponibilidad: `= this.availability`
- rol! Rol en el proyecto: `= this.role`   

--- 

## ¡Queremos conocerte mejor!

> [!important]- Este espacio es todo tuyo
> - ¿Cuáles son tus intereses y pasatiempos?
> - ¿Cómo prefieres que nos refiramos a ti? (nombre, pronombres, etc.)
> - Cualquier otro detalle que quieras compartir con nosotros.
> 
> ¡Nos encantará saber más sobre ti! :FasFaceSmile:

