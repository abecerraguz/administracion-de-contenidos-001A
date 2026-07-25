# Semana 03 - Personalizando un Sitio Web en WordPress

**Experiencia:** 2 | **Asignatura:** Administración de Contenidos

---

## Introducción

Esta semana se trabaja con los archivos propios de las publicaciones tipo post (blog). Se aprende a crear el primer sitio tipo blog con WordPress, personalizando `index.php` y `single.php` para controlar la estructura de listado y detalle de entradas.

---

## Temas Tratados

- Estructura de un blog de WordPress
- Creando un blog de WordPress desde cero
- Personalización de `index.php` y `content-index.php`
- Diagramando y creando `single.php` y `content-single.php`

## Conceptos Clave

- **index.php:** archivo principal que controla el listado de entradas del blog.
- **single.php:** plantilla que define la estructura de una entrada individual.
- **content-index.php / content-single.php:** archivos parciales que separan el contenido de la estructura.
- **Loop de WordPress:** bucle que itera sobre las entradas para mostrarlas (`while (have_posts()) : the_post()`).
- **Template Parts:** fragmentos de plantilla reutilizables cargados con `get_template_part()`.

## Resultado de Aprendizaje

- **RA1:** Evalúa estructura de contenidos de un proyecto digital mediante mapa de navegación.
- **RA3:** Arma plantilla personalizada en servidor local y remoto considerando criterios técnicos de diseño.

## Referencias y Recursos

- Material Guía Semana 3: `material-semana/material-guia-semana.pdf`
- [The Loop - WordPress Developer](https://developer.wordpress.org/themes/basics/the-loop/)
- [get_template_part()](https://developer.wordpress.org/reference/functions/get_template_part/)
