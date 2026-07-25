# Semana 03 - Ejercicios: Loop, index.php y single.php

**Proyecto integrador:** Blog Actualidad — Fase 3 de 8
**Tutoriales de referencia:** `06 - Get Template Parts: Cómo obtener los Posts` · `08 - Creando Header, Footer y Single Page`

> Esta semana se construye el núcleo del blog: el listado de entradas y el detalle de cada post.

---

## Ejercicio 1 — index.php con el Loop de WordPress

**Descripción:** Mostrar todas las entradas del blog usando el Loop base.

**Instrucciones:**

1. Abre `index.php` y reemplaza el contenido de prueba por la siguiente estructura:

```php
<?php get_header(); ?>

<main class="container my-4">
  <div class="row">

    <?php if ( have_posts() ) : while ( have_posts() ) : the_post(); ?>

      <article class="col-md-4 mb-4">
        <?php the_post_thumbnail('medium', array('class' => 'img-fluid')); ?>
        <h2><a href="<?php the_permalink(); ?>"><?php the_title(); ?></a></h2>
        <p class="text-muted"><?php echo get_the_date('d/m/Y'); ?></p>
        <p><?php the_excerpt(); ?></p>
        <a href="<?php the_permalink(); ?>" class="btn btn-primary">Leer más</a>
      </article>

    <?php endwhile; else : ?>
      <p>No se encontraron publicaciones.</p>
    <?php endif; ?>

  </div>
</main>

<?php get_footer(); ?>
```

2. Crea al menos **3 entradas** en el panel de WordPress con imagen destacada y extracto.
3. Verifica que el listado se muestra correctamente en el inicio del sitio.

---

## Ejercicio 2 — Template Part: separar la tarjeta de entrada

**Descripción:** Refactorizar el loop extrayendo el HTML de la tarjeta a un template part reutilizable.

**Instrucciones:**

1. Crea la carpeta `template-parts/` dentro de tu tema.
2. Crea el archivo `template-parts/content-card.php` con el HTML de la tarjeta (`<article>...</article>`) del ejercicio anterior.
3. En `index.php` reemplaza el bloque `<article>` por:

```php
<?php get_template_part('template-parts/content', 'card'); ?>
```

4. Verifica que el resultado visual es idéntico al ejercicio anterior.

---

## Ejercicio 3 — Crear single.php

**Descripción:** Crear la vista de detalle para una entrada individual.

**Instrucciones:**

1. Crea el archivo `single.php` con la siguiente estructura:

```php
<?php get_header(); ?>

<main class="container my-4">
  <div class="row justify-content-center">
    <div class="col-md-8">

      <?php if ( have_posts() ) : while ( have_posts() ) : the_post(); ?>

        <h1><?php the_title(); ?></h1>
        <p class="text-muted">
          Por <?php the_author(); ?> — <?php echo get_the_date('d/m/Y'); ?>
        </p>
        <?php the_post_thumbnail('large', array('class' => 'img-fluid mb-3')); ?>
        <div class="entry-content"><?php the_content(); ?></div>
        <p>Categorías: <?php the_category(', '); ?></p>
        <p>Etiquetas: <?php the_tags('', ', '); ?></p>
        <a href="<?php echo get_home_url(); ?>" class="btn btn-secondary mt-3">← Volver al blog</a>

      <?php endwhile; endif; ?>

    </div>
  </div>
</main>

<?php get_footer(); ?>
```

2. Haz clic en el enlace *Leer más* de una entrada y verifica que abre el single correctamente.

---

## Preguntas de Repaso

1. ¿Qué es el **Loop de WordPress** y por qué es fundamental en el desarrollo de temas?
2. ¿Qué diferencia hay entre `the_content()` y `the_excerpt()`?
3. ¿Para qué sirve `get_template_part()`? ¿Qué ventaja da frente a copiar y pegar el HTML?
4. ¿Qué archivo controla la vista de una entrada individual? ¿Y la de una página estática?
