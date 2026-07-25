# Semana 08 - Ejercicios: Taxonomías Personalizadas e Integración Final

**Proyecto integrador:** Blog Actualidad — Fase 8 de 8
**Tutoriales de referencia:** `09 - Creando el sidebar y consulta parametrizada` · `10 - Dejando dinámico el card del sidebar`

> Última fase de desarrollo. Se agregan taxonomías personalizadas al CPT Portafolio, se construye el sidebar dinámico y se integra todo el proyecto.

---

## Ejercicio 1 — Registrar una taxonomía personalizada para Portafolio

**Descripción:** Crear una taxonomía `tipo-proyecto` para clasificar el portafolio.

**Instrucciones:**

1. En `inc/post-types.php` (o un nuevo `inc/taxonomies.php`) agrega:

```php
add_action('init', 'blog_actualidad_register_taxonomies');

function blog_actualidad_register_taxonomies() {
    $labels = array(
        'name'          => 'Tipos de Proyecto',
        'singular_name' => 'Tipo de Proyecto',
        'all_items'     => 'Todos los tipos',
        'edit_item'     => 'Editar tipo',
        'add_new_item'  => 'Agregar nuevo tipo',
    );
    $args = array(
        'labels'       => $labels,
        'hierarchical' => true,  // comportamiento tipo categoría
        'public'       => true,
        'rewrite'      => array('slug' => 'tipo-proyecto'),
        'show_in_rest' => true,
    );
    register_taxonomy('tipo-proyecto', array('portafolio'), $args);
}
```

2. Si creaste `inc/taxonomies.php`, agrégalo al `require_once` en `functions.php`.
3. Desde el panel, crea los tipos: *Web*, *Diseño*, *Móvil*. Asigna cada proyecto a un tipo.

---

## Ejercicio 2 — Filtrar el portafolio por taxonomía con WP_Query

**Descripción:** Mostrar proyectos filtrados por tipo en la sección de portafolio.

**Instrucciones:**

1. En `index.php` modifica la query del portafolio para filtrar por tipo:

```php
$args_portafolio = array(
    'post_type'      => 'portafolio',
    'posts_per_page' => 3,
    'orderby'        => 'date',
    'order'          => 'DESC',
    'tax_query'      => array(
        array(
            'taxonomy' => 'tipo-proyecto',
            'field'    => 'slug',
            'terms'    => 'web',   // cambia para mostrar otro tipo
        ),
    ),
);
```

2. Muestra también los términos del proyecto con `get_the_terms()`:

```php
$tipos = get_the_terms(get_the_ID(), 'tipo-proyecto');
if ($tipos) {
    foreach ($tipos as $tipo) {
        echo '<span class="badge bg-secondary">' . esc_html($tipo->name) . '</span>';
    }
}
```

---

## Ejercicio 3 — Crear el sidebar dinámico

**Descripción:** Agregar un sidebar con las últimas entradas del blog usando una consulta parametrizada.

**Instrucciones:**

1. Crea `sidebar.php` en la raíz del tema:

```php
<aside class="col-md-3">
  <h4>Entradas recientes</h4>
  <?php
  $args_sidebar = array(
      'post_type'      => 'post',
      'posts_per_page' => 3,
      'orderby'        => 'date',
      'order'          => 'DESC',
  );
  $query_sidebar = new WP_Query($args_sidebar);
  if ($query_sidebar->have_posts()) :
      while ($query_sidebar->have_posts()) : $query_sidebar->the_post();
          get_template_part('template-parts/content', 'sidebar');
      endwhile;
      wp_reset_postdata();
  endif;
  ?>
</aside>
```

2. Crea `template-parts/content-sidebar.php` con el HTML de la tarjeta pequeña (imagen + título + fecha).
3. En `index.php` agrega `<?php get_sidebar(); ?>` en la columna lateral.

---

## Integración Final del Proyecto

Verifica que tu tema **Blog Actualidad** tiene todas las partes funcionando:

- [ ] Slider dinámico en el home (CPT Slider + ACF)
- [ ] Listado de entradas del blog con template parts
- [ ] Sección de portafolio filtrada por taxonomía
- [ ] Sidebar con entradas recientes
- [ ] Menú de navegación responsivo
- [ ] `archive.php` para ver entradas por categoría
- [ ] `single.php` para leer entradas completas
- [ ] `page.php` para las páginas estáticas
- [ ] Sitio desplegado en cPanel

---

## Preguntas de Repaso

1. ¿Qué diferencia hay entre una taxonomía jerárquica (`hierarchical => true`) y una plana?
2. ¿Qué hace `get_the_terms()` y qué diferencia tiene con `the_category()`?
3. ¿Por qué es importante `wp_reset_postdata()` cuando usas múltiples `WP_Query` en la misma página?
4. ¿Qué pasos hay que repetir en cPanel para reflejar los cambios del tema después de esta semana?
