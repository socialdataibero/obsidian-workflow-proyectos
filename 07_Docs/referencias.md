# :LiFileCheck: ¿Cómo citar?

---
> [!important]+ **¿Cómo se manejan las referencias dentro del proyecto?**
> Todas las referencias de los proyectos se manejan con `Zotero`. Dentro del flujo de trabajo en obsidian, se usa el plugin `Zotero Integration`.
> 
> Sigue estas instrucciones para realizar todas las configuraciones necesarias de estas herramientas, y aprender a utilizarlas.

---
## :RiInstallFill: **1. Instalaciones externas necesarias**

- Asegúrate de tener instalado **Zotero**.
- Instala el plugin [Better BibTeX para Zotero](https://retorque.re/zotero-better-bibtex/installation/), necesario para gestionar correctamente las citas.

---
## :FasScrewdriverWrench: **2. Configuración de Zotero**

- Asegúrate de que Zotero está instalado y que esté abierto en tu computadora.
- Revisa que tengas seleccionado el **estilo de bibliografía** del proyecto:  **APA 7th**.
- Configura un **Quick Copy Style** en Zotero:
    - En Zotero, ve a **Editar > Preferencias > Exportar**.
    - Asegúrate de tener esta configuración:
	    ![[zotero_config.png]]

---
## :LiNewspaper: **3. Uso de Zotero Integrations**

> [!warning]  
> Asegúrate de tener abierto e instalado _**Zotero**_ para poder usar **Zotero Integrations**.
### 3.1 Insertar referencias en el texto

- Para insertar una referencia dentro del texto (_en linea_) usa `ALT + L`. 
- Este comando debería abrir una ventana en Zotero como la siguiente:
	![[zotero_bar.png]]
- Busca la(s) referencias que desees citar en el texto e insértalas. Deberías obtener un texto como el siguiente: _(Du et al., 2022)_ 

### 3.2 Insertar bibliografía completa

- Para insertar la bibliografía completa usa `ALT + B`. 
- Este comando debería abrir la ventana de búsqueda de Zotero.
- Busca la(s) referencias que usaste e insértalas. Deberías obtener un texto como el siguiente: 

> [!example]- Ejemplo de bibliografía
> Asst. Professor, Department of Computer Science, King Khalid University, Abha, Kingdom of Saudi Arabia., Sharma, Dr. N., Iqbal, S. I. M., & Department of Computer Science, King Khalid University, Abha, Kingdom of Saudi Arabia. (2023). Applying Decision Tree Algorithm Classification and Regression Tree (CART) Algorithm to Gini Techniques Binary Splits. _International Journal of Engineering and Advanced Technology_, _12_(5), 77–81. [https://doi.org/10.35940/ijeat.E4195.0612523](https://doi.org/10.35940/ijeat.E4195.0612523)
> 
>Du, K.-L., Leung, C.-S., Mow, W. H., & Swamy, M. N. S. (2022). Perceptron: Learning, Generalization, Model Selection, Fault Tolerance, and Role in the Deep Learning Era. _Mathematics_, _10_(24), 4730. [https://doi.org/10.3390/math10244730](https://doi.org/10.3390/math10244730)

## 3.3 Clasificar referencias por colores 

1. En Zotero, abre el archivo `.pdf`  y subraya información según el [código de colores](07_Docs/codigo_colores).
2. Añade notas y etiquetas a los subrayados si es necesario.
3. En Obsidian, usa `ALT + I` para desplegar la barra de búsqueda de Zotero.
4. Busca la referencia subrayada y presiona `Enter`.
5. Una nota con el nombre del `citekey` de la referencia se insertará automáticamente en la carpeta `Bibliografia`, incluyendo tus anotaciones y metadatos.
6. _¡Listo!_, ahora tienen una nota asignada con la información clasificada por colores, junto con etiquetas y anotaciones.  
