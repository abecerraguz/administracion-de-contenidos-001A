# Semana 04 - Ejercicios: archive.php y Menú de Navegación

**Proyecto integrador:** Blog Actualidad — Fase 4 de 8
**Tutoriales de referencia:** `07 - Creando el Nav` · `11 - Archivo archive.php y taxonomías`

> Esta semana se crea la página de archivo por categoría y se integra el menú de navegación al tema.

---

## Ejercicio 1 — Registrar y mostrar el menú de navegación

**Descripción:** Agregar un menú de navegación funcional al header del tema.

**Instrucciones:**

1. Verifica que en `functions.php` ya está registrado el menú `primary` (semana 2). Si no, agrégalo:

```php
register_nav_menus(array(
    'primary' => __('Menú Principal', 'blog-actualidad'),
));
```

2. En el panel de WordPress ve a **Apariencia → Menús**, crea un menú con enlaces a: *Inicio*, las categorías que creaste y la página *Sobre mí*. Asígnalo a la ubicación **Menú Principal**.
3. Abre `header.php` y agrega dentro del `<nav>` la llamada al menú:

```php
<?php wp_nav_menu(array(
    'theme_location' => 'primary',
    'menu_class'     => 'navbar-nav ms-auto',
    'container'      => false,
    'fallback_cb'    => false,
)); ?>
```

4. Aplica clases de Bootstrap para que el menú sea responsivo (navbar, navbar-expand-lg, etc.).

---

## Ejercicio 2 — Crear archive.php

**Descripción:** Mostrar entradas filtradas por categoría al hacer clic en un enlace del menú.

**Instrucciones:**

1. Crea el archivo `archive.php` en la raíz del tema:

```php
<?php get_header(); ?>

<main class="container my-4">
  <h1 class="mb-4">
    Archivo: <?php single_cat_title(); ?>
  </h1>
  <div class="row">

    <?php if ( have_posts() ) : while ( have_posts() ) : the_post(); ?>
      <?php get_template_part('template-parts/content', 'card'); ?>
    <?php endwhile; else : ?>
      <p>No hay entradas en esta categoría.</p>
    <?php endif; ?>

  </div>
</main>

<?php get_footer(); ?>
```

2. Haz clic en una categoría desde el menú y verifica que muestra solo las entradas de esa categoría.
3. Agrega la paginación al final del loop con `the_posts_navigation()`.

---

## Ejercicio 3 — Crear page.php

**Descripción:** Crear la plantilla para páginas estáticas (como *Sobre mí*).

**Instrucciones:**

1. Crea `page.php` con una estructura similar a `single.php` pero sin mostrar categorías ni etiquetas.
2. Accede a la página *Sobre mí* y verifica que usa `page.php`.
3. Usa la condicional `is_page()` en `header.php` para aplicar una clase CSS diferente cuando se está en una página.

---

## Preguntas de Repaso

1. ¿Qué diferencia hay entre `wp_nav_menu()` y `wp_page_menu()`?
2. ¿Qué archivo de WordPress controla la vista de archivos por categoría, etiqueta y fecha?
3. ¿Qué hace `single_cat_title()`? ¿Dónde más podrías usarlo?
4. ¿Qué hace `the_posts_navigation()` y cuándo es importante incluirla?
