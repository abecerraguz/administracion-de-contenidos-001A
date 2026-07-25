# Semana 06 - Ejercicios: Custom Post Types y WP_Query

**Proyecto integrador:** Blog Actualidad — Fase 6 de 8
**Tutoriales de referencia:** `13 - Mejora en functions.php` · `14 - Creación de Post Type e incorporación en functions.php`

> Esta semana se crea el primer Custom Post Type del proyecto y se usan consultas personalizadas para mostrar su contenido.

---

## Ejercicio 1 — Organizar functions.php con includes

**Descripción:** Separar el archivo `functions.php` en módulos para mantener el código limpio.

**Instrucciones:**

1. Crea la carpeta `inc/` dentro de tu tema.
2. Crea el archivo `inc/enqueue.php` y mueve allí la función `blog_actualidad_scripts()`.
3. Crea el archivo `inc/setup.php` y mueve allí la función `blog_actualidad_setup()`.
4. En `functions.php` deja solo los `require_once` que cargan los archivos:

```php
<?php
require_once get_template_directory() . '/inc/setup.php';
require_once get_template_directory() . '/inc/enqueue.php';
require_once get_template_directory() . '/inc/post-types.php'; // para el siguiente ejercicio
```

5. Verifica que el sitio sigue funcionando correctamente.

---

## Ejercicio 2 — Crear el Custom Post Type *Portafolio*

**Descripción:** Registrar un CPT para mostrar trabajos o proyectos del blog.

**Instrucciones:**

1. Crea el archivo `inc/post-types.php` con el siguiente código:

```php
<?php

add_action('init', 'blog_actualidad_register_cpt');

function blog_actualidad_register_cpt() {
    $labels = array(
        'name'          => 'Portafolio',
        'singular_name' => 'Proyecto',
        'add_new_item'  => 'Agregar nuevo proyecto',
        'edit_item'     => 'Editar proyecto',
        'all_items'     => 'Todos los proyectos',
        'not_found'     => 'No se encontraron proyectos',
    );
    $args = array(
        'labels'      => $labels,
        'public'      => true,
        'has_archive' => true,
        'supports'    => array('title', 'editor', 'thumbnail', 'excerpt'),
        'rewrite'     => array('slug' => 'portafolio'),
        'show_in_rest'=> true,
    );
    register_post_type('portafolio', $args);
}
```

2. Refresca los permalinks desde **Configuración → Enlaces permanentes** (guarda sin cambiar nada).
3. Crea **3 proyectos** desde el nuevo menú **Portafolio** en el panel.

---

## Ejercicio 3 — Mostrar el CPT con WP_Query

**Descripción:** Crear una sección en el index que muestre los últimos proyectos del portafolio.

**Instrucciones:**

1. Abre `index.php` y agrega debajo del loop principal la siguiente consulta:

```php
<section class="container my-5">
  <h2>Proyectos del Portafolio</h2>
  <div class="row">

  <?php
  $args_portafolio = array(
      'post_type'      => 'portafolio',
      'posts_per_page' => 3,
      'orderby'        => 'date',
      'order'          => 'DESC',
  );
  $query_portafolio = new WP_Query($args_portafolio);

  if ($query_portafolio->have_posts()) :
      while ($query_portafolio->have_posts()) : $query_portafolio->the_post();
  ?>
      <div class="col-md-4">
          <?php the_post_thumbnail('medium', array('class' => 'img-fluid')); ?>
          <h3><a href="<?php the_permalink(); ?>"><?php the_title(); ?></a></h3>
          <p><?php the_excerpt(); ?></p>
      </div>
  <?php
      endwhile;
      wp_reset_postdata();
  else :
      echo '<p>No hay proyectos aún.</p>';
  endif;
  ?>

  </div>
</section>
```

2. Verifica que los 3 proyectos se muestran correctamente en el inicio del blog.

---

## Preguntas de Repaso

1. ¿Por qué es importante llamar a `wp_reset_postdata()` al terminar un `WP_Query`?
2. ¿Qué hace `show_in_rest => true` en el registro del CPT?
3. ¿Por qué conviene separar `functions.php` en módulos con `require_once`?
4. ¿Qué diferencia hay entre el Loop global de WordPress y una consulta con `WP_Query`?
