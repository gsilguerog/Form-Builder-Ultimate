# 🏗️ Form Builder Ultimate (Drag & Drop)
***Generador de formularios Bootstrap realizado con IA.***

![IMAGE](https://github.com/gsilguerog/Form-Builder-Ultimate/blob/main/UFB.PNG?raw=true)

Form Builder Ultimate es una herramienta web client-side (sin backend) que permite crear formularios HTML complejos visualmente utilizando una interfaz de "arrastrar y soltar" (Drag & Drop). Está construido sobre Bootstrap 5 y utiliza SortableJS para la gestión del movimiento de elementos.

El objetivo principal es prototipar y generar código HTML limpio y listo para producción de manera rápida, eliminando la necesidad de escribir manualmente el boilerplate de formularios.

## 🚀 Características Principales
- Drag & Drop Fluido: Arrastra componentes desde la barra lateral al lienzo.

- Edición Intuitiva (Click-to-Edit): Haz clic en cualquier componente para abrir sus configuraciones. No hace falta buscar botones pequeños; todo el componente es interactivo.

Componentes Soportados:

- Estructura: Grids (Filas/Columnas anidables) y Tablas dinámicas.

- Inputs: Texto, Email, Textarea, Fechas, Password (configurable).

- Selección: Selects (Dropdowns), Radio Buttons, Checkboxes.

- Acción: Botones, Switches.

- Gestión de Propiedades:

- Edición de etiquetas (Labels), nombres de variables (Name attributes) y Placeholders.

- Atributos HTML5: `Required`, `Readonly`, `Hidden`.

- Gestión dinámica de opciones para Selects y Radios.

- Exportación de Código: Genera y limpia el código HTML resultante, listo para copiar y pegar en tu proyecto.

## 🛠️ Tecnologías Utilizadas
HTML5 & CSS3: Estructura y diseño base.

Bootstrap 5.3: Framework de estilos para asegurar que los formularios sean responsivos y estéticos (utiliza clases nativas de BS como `form-control`, `row`, `col`, etc.).

JavaScript (Vanilla): Toda la lógica de negocio, manipulación del DOM y gestión de eventos.

SortableJS: Librería ligera para habilitar la funcionalidad de arrastrar y soltar.

## 🧠 Arquitectura y Lógica del Proyecto
Este proyecto utiliza un enfoque de manipulación directa del DOM. Aquí están los conceptos clave para entender el código:

1. Sistema de Wrappers (Envoltorios)
Cada componente que se suelta en el lienzo no es solo el input HTML, sino que está encapsulado en un `div` contenedor (`.form-component-wrapper`.

Función: Este wrapper maneja los eventos de click para la edición y contiene visualmente el botón de eliminar (que solo aparece en hover).

UX: Usamos pointer-events: none en los inputs internos dentro del lienzo para que, al hacer clic en un "input de texto", no se ponga el foco en el input, sino que se dispare el evento de edición del wrapper.

2. Gestión de Eventos y stopPropagation
Uno de los retos más grandes en constructores visuales es la anidación (ej. un input dentro de una columna, dentro de un grid).

Solución: Al hacer clic en un componente hijo, utilizamos `event.stopPropagation()` para evitar que el evento "burbujee" hacia los contenedores padres. Esto asegura que si editas un input, no se abra accidentalmente la configuración de la fila (Grid) que lo contiene.

3. Lógica de "Guardar Cambios"
El modal de edición no reconstruye el componente desde cero. En su lugar:

Identifica el ID único del wrapper activo.

Busca los elementos internos (labels, inputs) mediante selectores CSS.

Inyecta los nuevos valores directamente en el DOM.

Si el campo de "Placeholder" se deja vacío, el atributo se elimina del HTML para mantener el código limpio.

4. Exportación Limpia
Al exportar, el script:

Clona el lienzo completo.

Elimina las clases de utilidad del constructor (bordes punteados, clases de drag & drop).

Elimina los wrappers de edición y los botones de eliminar.

Devuelve un HTML puro de Bootstrap.

## 📦 Instalación y Uso
Este proyecto no requiere instalación de dependencias de Node.js ni servidores.

Clonar el repositorio:

```
git clone https://github.com/tu-usuario/form-builder-ultimate.git
```
Ejecutar: Simplemente abre el archivo `index.html` en tu navegador web favorito (Chrome, Firefox, Edge).

## 🎮 Cómo usar
- **Arrastrar:** Selecciona un elemento del panel izquierdo y arrástralo al lienzo central.

- **Estructurar:** Puedes arrastrar un "Grid" primero para dividir el formulario en columnas y luego soltar inputs dentro de esas columnas.

- **Editar:** Haz clic sobre cualquier elemento en el lienzo para cambiar su etiqueta, nombre, obligatoriedad, etc.

- **Eliminar:** Pasa el mouse sobre un elemento y haz clic en el icono de basura rojo que aparece.

- **Exportar:** Haz clic en el botón verde "Ver HTML", copia el código y úsalo en tu aplicación.

## 🤝 Contribución
Las contribuciones son bienvenidas. Si tienes ideas para mejorar la lógica de anidación o agregar nuevos componentes (como subida de archivos), siéntete libre de abrir un Pull Request.

## 📄 Licencia
Este proyecto está bajo la Licencia MIT - eres libre de usarlo y modificarlo para proyectos personales o comerciales.

## 🌎 Preview
https://gsilguerog.github.io/Form-Builder-Ultimate/FBU/
