# Semana 02 - Ejercicios: Iniciando el Tema Blog Actualidad

**Proyecto integrador:** Blog Actualidad — Fase 2 de 8
**Tutoriales de referencia:** `00 - Archivos base` · `04 - Iniciando un Theme` · `05 - Header, Footer, Hook y Encolamiento`

> Esta semana se crea la estructura mínima del tema y se configura el encolamiento de estilos y scripts.

---

## Ejercicio 1 — Estructura mínima del tema

**Descripción:** Crear los archivos obligatorios para que WordPress reconozca el tema.

**Instrucciones:**

1. En tu instalación local, navega a `wp-content/themes/` y crea la carpeta `blog-actualidad`.
2. Crea el archivo `style.css` con la siguiente meta información:

```css
/*
  Theme Name: Blog Actualidad
  Theme URI: http://localhost/blog-actualidad
  Author: Tu Nombre
  Author URI: http://example.com
  Description: Tema WordPress desarrollado desde cero en la asignatura Administración de Contenidos.
  Version: 1.0
  License: GNU General Public License v2 or later
  License URI: http://www.gnu.org/licenses/gpl-2.0.html
  Text Domain: blog-actualidad
*/
```

3. Crea el archivo `index.php` con un `<h1>Hola desde Blog Actualidad</h1>` de prueba.
4. Agrega una imagen `screenshot.png` (1200×900 px) para la vista previa del tema.
5. Activa el tema desde **Apariencia → Temas** en el panel de WordPress.

---

## Ejercicio 2 — Crear functions.php con encolamiento

**Descripción:** Registrar el tema y encolar correctamente los archivos CSS y JS.

**Instrucciones:**

1. Crea el archivo `functions.php` con el siguiente código base:

```php
<?php

function blog_actualidad_setup() {
    add_theme_support('post-thumbnails');
    add_theme_support('title-tag');
    register_nav_menus(array(
        'primary' => __('Menú Principal', 'blog-actualidad'),
    ));
}
add_action('after_setup_theme', 'blog_actualidad_setup');

function blog_actualidad_scripts() {
    wp_enqueue_style('bootstrap-css',
        get_template_directory_uri() . '/assets/css/bootstrap.min.css');
    wp_enqueue_style('main-styles',
        get_template_directory_uri() . '/assets/css/main.css');
    wp_enqueue_script('bootstrap-js',
        get_template_directory_uri() . '/assets/js/bootstrap.bundle.min.js',
        array('jquery'), null, true);
    wp_enqueue_script('main-scripts',
        get_template_directory_uri() . '/assets/js/main.js',
        array('jquery'), null, true);
}
add_action('wp_enqueue_scripts', 'blog_actualidad_scripts');
```

2. Crea la carpeta `assets/css/` y coloca un `main.css` con estilos básicos de body.
3. Crea la carpeta `assets/js/` y coloca un `main.js` con un `console.log('Blog Actualidad OK');`.
4. Copia los archivos de Bootstrap desde los archivos base del tutorial `00`.

---

## Ejercicio 3 — Crear header.php y footer.php

**Descripción:** Separar la estructura HTML en archivos reutilizables.

**Instrucciones:**

1. Crea `header.php` con la estructura `<!DOCTYPE html>`, `<html>`, `<head>` y llama a `<?php wp_head(); ?>` justo antes del `</head>`.
2. Crea `footer.php` con el cierre `</body></html>` y llama a `<?php wp_footer(); ?>` antes de `</body>`.
3. En `index.php` reemplaza tu HTML manual por:

```php
<?php get_header(); ?>
  <h1><?php bloginfo('name'); ?></h1>
  <p><?php bloginfo('description'); ?></p>
<?php get_footer(); ?>
```

4. Verifica en el inspector del navegador que Bootstrap y main.css cargan correctamente.

---

## Preguntas de Repaso

1. ¿Por qué se usa `wp_enqueue_style()` en lugar de una etiqueta `<link>` directa en el HTML?
2. ¿Qué rol cumple el hook `wp_enqueue_scripts`?
3. ¿Qué diferencia hay entre `get_template_directory_uri()` y `get_stylesheet_uri()`?
4. ¿Para qué sirve `wp_head()` y `wp_footer()`? ¿Qué pasaría si los eliminamos?
