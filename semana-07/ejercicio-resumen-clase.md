# Semana 07 - Ejercicios: Slider con ACF y Custom Post Type

**Proyecto integrador:** Blog Actualidad — Fase 7 de 8
**Tutoriales de referencia:** `15 - Creación del Post Type Slider y dejarlo dinámico desde el post slider`

> Esta semana se crea un CPT Slider con campos personalizados usando ACF, y se muestra dinámicamente en el frontend.

---

## Ejercicio 1 — Instalar ACF y crear el CPT Slider

**Descripción:** Agregar el plugin ACF y crear el tipo de contenido para el slider del home.

**Instrucciones:**

1. En el panel de WordPress ve a **Plugins → Añadir nuevo** y busca **Advanced Custom Fields**. Instálalo y actívalo.
2. Agrega en `inc/post-types.php` el registro del CPT Slider:

```php
function blog_actualidad_register_cpt_slider() {
    $args = array(
        'labels'      => array(
            'name'          => 'Sliders',
            'singular_name' => 'Slide',
            'add_new_item'  => 'Agregar nuevo slide',
            'all_items'     => 'Todos los slides',
        ),
        'public'      => true,
        'has_archive' => false,
        'supports'    => array('title', 'thumbnail'),
        'rewrite'     => array('slug' => 'slider'),
        'show_in_rest'=> true,
    );
    register_post_type('slider', $args);
}
add_action('init', 'blog_actualidad_register_cpt_slider');
```

3. Refresca los permalinks (**Configuración → Enlaces permanentes**).

---

## Ejercicio 2 — Crear campos personalizados con ACF

**Descripción:** Agregar campos extra al CPT Slider para controlar el contenido dinámicamente.

**Instrucciones:**

1. Ve a **ACF → Añadir nuevo** en el panel y crea un grupo de campos llamado **Datos del Slider**.
2. Agrega los siguientes campos:
   - `subtitulo` — tipo: Texto
   - `url_boton` — tipo: URL
   - `texto_boton` — tipo: Texto
3. En **Reglas de ubicación** asigna el grupo al tipo de contenido **Slider**.
4. Crea **3 slides** desde el panel, completando título, imagen destacada y los campos ACF.

---

## Ejercicio 3 — Mostrar el Slider dinámico en el frontend

**Descripción:** Usar `WP_Query` y las funciones `get_field()` de ACF para mostrar el slider en el home.

**Instrucciones:**

1. En `header.php` (o al inicio de `index.php`) agrega el siguiente bloque del slider:

```php
<?php
$args_slider = array(
    'post_type'      => 'slider',
    'posts_per_page' => -1,
    'orderby'        => 'menu_order',
    'order'          => 'ASC',
);
$query_slider = new WP_Query($args_slider);
?>

<div id="carouselSlider" class="carousel slide" data-bs-ride="carousel">
  <div class="carousel-inner">

  <?php $count = 0; ?>
  <?php if ($query_slider->have_posts()) : while ($query_slider->have_posts()) : $query_slider->the_post(); ?>

    <div class="carousel-item <?php echo $count === 0 ? 'active' : ''; ?>">
      <?php the_post_thumbnail('full', array('class' => 'img-fluid w-100')); ?>
      <div class="carousel-caption">
        <h2><?php the_title(); ?></h2>
        <p><?php echo get_field('subtitulo'); ?></p>
        <a href="<?php echo get_field('url_boton'); ?>" class="btn btn-light">
          <?php echo get_field('texto_boton'); ?>
        </a>
      </div>
    </div>

  <?php $count++; endwhile; wp_reset_postdata(); endif; ?>

  </div>
  <button class="carousel-control-prev" type="button" data-bs-target="#carouselSlider" data-bs-slide="prev">
    <span class="carousel-control-prev-icon"></span>
  </button>
  <button class="carousel-control-next" type="button" data-bs-target="#carouselSlider" data-bs-slide="next">
    <span class="carousel-control-next-icon"></span>
  </button>
</div>
```

2. Verifica que el slider muestra las imágenes y el contenido de cada slide dinámicamente.
3. Agrega un cuarto slide desde el panel y confirma que aparece sin modificar el código.

---

## Preguntas de Repaso

1. ¿Qué es un **metabox** y cómo se relaciona con ACF?
2. ¿Qué diferencia hay entre `get_field()` y `the_field()` en ACF?
3. ¿Por qué el CPT Slider tiene `has_archive => false`?
4. ¿Qué ventaja da usar ACF frente a crear metaboxes manualmente con `add_meta_box()`?
