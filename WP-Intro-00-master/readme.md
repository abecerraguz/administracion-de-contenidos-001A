<section>

# FUNDAMENTOS DE PHP PARA DESARROLLO DE THEMES EN WORDPRESS

![Landing More Themes](screenshot_landing.png)

PHP (acrónimo recursivo de PHP: Hypertext Preprocessor) es un lenguaje de código abierto muy popular especialmente adecuado para el desarrollo web y que puede ser incrustado en HTML.


## PARA ESCRIBIR PHP
```php

	<?php ?>

```

## USO DE COMENTARIOS
```php

	<?php
		//Comentarios en Line
		/*Comentarios en Bloque*/
	;?>

```

## SALIDA POR PANTALLA PHP
```php

	<?php
		print 'Hola';
		echo  'Hola', 'Hola de nuevo';
	?>

```

## VARIABLES TIPO CADENAS O STRING
```php

	<?php
		$nombre 	= 'Roberto';
		$apellido   = 'Rojas';
		echo "$nombre, $apellido"; // imprime "Roberto, Rojas"

		$4nombre    = 'aun no';   // inválido; comienza con un número
		$_4nombre   = 'aun no';  // válido; comienza con un carácter de subrayado
	?>

```

## VARIABLES TIPO NUMEROS INT
```php

	<?php
		$x = 5985;
		var_dump(is_int($x));//Imprime bool(true)
		echo '</br>';
		$x = 59.85;//Imprime bool(false)
		var_dump(is_int($x));
	?>

```

## VARIABLES TIPO NUMEROS FLOAT
```php

	<?php
		$x = 10.365;
		var_dump(is_float($x));
	?>

```

## ARRAYS
```php

	<?php
		// Array Indexado el orden es a través del indice.
		$cars = array("Volvo", "BMW", "Toyota");
		echo "Me gusta el " . $cars[0] . ", " . $cars[1] . " and " . $cars[2] . ".";
	?>

	<?php
		// Array Asociativo, están ordenados en vase a una llave y el valor asociado a la llave.
		$color = array('pasto' => 'Verde', 'cielo' => 'Celeste', 'mar' => 'Azul');
		echo 'El color que indicaremos será el siguiente:'.$color['pasto'];
	?>


	<?php
		// Array Multidimencional Arreglos dentro de un Arreglo
		$frutas array(
		
			array('Manzana','rojo','12'),
			array('Naranja','naranjo','10'),
			array('Pera','verde','18')

			echo $frutas[0][0].' Su color es:'.$frutas[0][1].' y quedan disponibles '.$frutas[0][1];
		)
	?>


```

## OPERADORES DE COMPARACIÓN
~~~html
==	Igual			$x == $y 
===	Identico		$x === $y 
!=	Distinto		$x != $y
<>	Distinto  		$x <> $y
!==	No es identico	$x !== $y
>	Mayor que		$x > $y
<	Menor que		$x < $y
>=	Mayor igual		$x >= $y
<=	Menor Igual 	$x <= $y
~~~

## OPERADORES DE INCREMENTO Y DECREMENTO
~~~html
++$x	Pre-incrementa
$x++	Post-incrementa
--$x	Pre-decrementa
$x--	Post-decrementa
~~~

## CONCATENAR VARIABLES
```php

	<?php 
		$numeroUno = 18;
		$numeroDos = ' de Septiembre'
		echo '<h1>'.$numeroUno.$numeroDos.'</h1>';
	?>

```

## ESTRUCTURA DE CONTROL MÁS UTILIZADAS EN WORDPRESS

### Condicional IF
```php

	<?php
		$a = 100;
		$b = 0;
		if($a > $b){
		echo "a es mayor que b";
		}
	?>

```

### Bucle o Loop While
```php

	<?php
		$a = 0;
		while($a <= 10){
		$a++;
		echo '<h1>'.$a.'</h1>';
		}
	?>

```

### Bucle o Loop Do While
```php

	<?php
		// Se ejecuta primero.
		$a = 1;
		do{
			echo 'El número es:'.$a.'<br>';
			$a++
		// Luego evalúa.
		}while($a <= 10);
	?>

```

### Bucle o Loop For
```php

	<?php  
		for ($x = 0; $x <= 10; $x++) {
		echo 'El número es:'.$x.'<br>';
		}
	?> 

```

### Bucle o Loop Foreach
```php

	<?php 
		//Recorre un array
		$frutas = array('Manzana','Pera','Naranja','Frutilla'); 
		foreach ($frutas as $valor) {
		echo "La fruta es:'.$frutas.'<br>';
		}
	?> 

```


# INICIO DE UN THEME BASICO

- Descarga WordPress desde <https://www.wordpress.org/> debes instalarlo
> Hint: Descargar HTML para trabajar THEMES [https://drive.google.com/file/d/1b3nM58QzpEBOTiJPn01dU1ezQXO0S9lX/view?usp=sharing](https://drive.google.com/file/d/1b3nM58QzpEBOTiJPn01dU1ezQXO0S9lX/view?usp=sharing)


### Para crear un Theme desde cero, se necesita como minimo:
~~~

	-wp-content/themes/mi_tema
	|
	|– index.php  
	|– style.css
	|– screenshot.png
	|– function.php

~~~

### Taxonomía de un theme.
~~~

-wp-content/themes/themes_lab02
	|
	|--assets/
	|    |
	|    |
	|    |
	|	img/
	|	|--img.jpg
	|	|--img.png
	|	|--img.gif
	|
	|   js/
	|	|--___.js--Archivos js que se requieren según la necesidad del proyecto
	|	|--___.js
	|	|--___.js
	|
	|   css/
	|	|--___.css--Archivos css que se requieren según la necesidad del proyecto
	|	|--___.css
	|	|--___.css
	|
	|– index.php--Pagina de inicio o de partida de un themes.
	|
	|– function.php--Guarda todas las funciones de worpdress. 
	|
	|– style.css--Hoja de estilo de la raiz del themes, contiene la meta información del themes.
	|
	|– screenshot.png--Imagen 1200px de ancho por 900px de alto.
	|
	|– page.php--Muestra el detalle de la información de las páginas (page).
	|		|--page-nombre.php --Distintas plantillas de page,requieren comentario.
	|		|--page-nombre-de-la-plantilla.php
	|		|--page-nombre-de-la-plantilla.php
	|
	|– single.php--Muestra el detalle de la información de las publicaciones (post).
	|		|--single-nombre.php --Distintas plantillas de single,requieren comentario.
	|		|--single-nombre.php
	|		|--single-nombre.php
	|
	|– header.php--Contiene la información superior de head de mis páginas.
	|
	|– footer.php--Contiene la información del footer de mis páginas.
	|
	|– footer.php--Contiene la información del footer de mis páginas.

~~~
### ENCOLAMIENTO DE ARCHIVOS CSS Y JS MINIMO VIABLE

#### function.php

```php

	function my_theme_scripts() {
		// Encolar Bootstrap CSS
		wp_enqueue_style('bootstrap-css', get_template_directory_uri() . '/assets/librerias/css/bootstrap.min.css');

		// Encolar el archivo CSS personalizado
		wp_enqueue_style('main-styles', get_template_directory_uri() . '/assets/librerias/css/main.css');

		// Encolar Bootstrap JS (bundle incluye Popper.js)
		wp_enqueue_script('bootstrap-js', get_template_directory_uri() . '/assets/librerias/js/bootstrap.bundle.min.js', array('jquery'), null, true);

		// Encolar el archivo JavaScript personalizado
		wp_enqueue_script('main-scripts', get_template_directory_uri() . '/assets/librerias/js/main.js', array('jquery'), null, true);
	}

	add_action('wp_enqueue_scripts', 'my_theme_scripts');


```

### META INFORMACION DEL TEMA

#### style.css

```css

	/*

		Theme Name: My Theme v-1
		Theme URI: http://localhost/wp_inicio
		Author: Alejandro Becerra
		Author URI: http://example.com
		Description: Un tema WordPress básico de inicio.
		Version: 1.0
		License: GNU General Public License v2 or later
		License URI: http://www.gnu.org/licenses/gpl-2.0.html
		Text Domain: my-theme
		Tags: custom-background, custom-logo, custom-menu, featured-images, threaded-comments, translation-ready

	*/

```

### COMETARIOS PLANTILLAS

#### page-nosotros.php

```php

	<?php 
		/**
		 * Template Name: Page Nosotros
		 * Template Post Type: page
		*/
	?> 

```

#### single-servicios.php

```php

	<?php 
		/*
		* Template Name: Single Servicios
		* Template Post Type: post
		*/
	?> 

```


# PARA LLAMAR AL HEAD (TIPO INCLUDE)
## URL DE REFERENCIA
[https://developer.wordpress.org/reference/functions/get_header/](https://developer.wordpress.org/reference/functions/get_header/)

```php

	<?php get_header();?>

```

# PARA LLAMAR AL SIDEBAR (TIPO INCLUDE)
## URL DE REFERENCIA
[https://developer.wordpress.org/reference/functions/get_sidebar/](https://developer.wordpress.org/reference/functions/get_sidebar/)

```php

	<?php get_sidebar();?>

```

# PARA LLAMAR AL FOOTER (TIPO INCLUDE)
## URL DE REFERENCIA
[https://developer.wordpress.org/reference/functions/get_footer/](https://developer.wordpress.org/reference/functions/get_footer/)

```php

	<?php get_footer();?>

```

# HEADER Y FOOTER HOOK

## URL DE REFERENCIA
`https://codex.wordpress.org/Function_Reference/wp_head`

```php

	<?php 
		...
		/* Siempre inserte wp_head() justo antes de cerrar el </head>
		* wp_head(), ayuda a los complementos como plugins inserten
		* sus estilos, jquey, script, estos son complementos necesarios para su correcto funcionamiento.
		* También es importante para insertar correctamente los CSS, Jquery y complemnetos del Themes,
		* desde una funcion desde el archivo function.php
		*/
		wp_head();
	?>

```

## URL DE REFERENCIA
[https://codex.wordpress.org/Function_Reference/wp_footer](https://codex.wordpress.org/Function_Reference/wp_footer)

```php

	<?php 
		...
		/* Siempre inserte wp_footer() justo antes de cerrar el </body>
		* wp_head(), ayuda a que complementos como plugins inserten
		* sus estilos, jquey, script, complementos necesarios para su correcto funcionamiento.
		* También es importante para insertar correctamente los CSS, Jquery y complemnetos del Themes,
		* desde una funcion desde el archivo function.php
		*/
		wp_footer();
	?>

```

## LOOP BASE DE WORDPRESS
```php

		<?php 
			// Si existe publicación.
			if(have_posts()){
				//Muestra las publicaciones.
				while (have_posts()):the_post(); 
				{
					//get_the_title(), recupera el título de la publicación
					echo '<h1>'.get_the_title().'</h1>';

					//the_post_thumbnails(), recupera la imagen destacada.
					echo the_post_thumbnail('thumbnail','class=img');

					//Recupera la fecha de la publicación
					echo '<h5>'.get_the_date().'</h5>';

					// the_content(), recupera el contenido de la publicación.
					echo the_content();

					//the_excerpt(), recupera el resumen de la publicación.
					echo the_content();

					// get_the_permalink(), recupera el enlace permanente
					echo '<a href="'.get_the_permalink().'" target="_self" title="'.get_the_title().'">Ver publicación</a>';     
				}
				endwhile;
			}else{
				echo '<h3>Lo sentimos no existe publicacion</h3>';
			}
		?>

```

## POST_TYPE DE WORDPRESS CONDICIONADO A UNA CATEGORÍA
```php

	<?php 

		$argsXXXX = array(
		'post_type'	   => 'xxxx',
		'category_name'  => 'xxxx'
		'posts_per_page' =>  -1,
		'orderby'        => 'title',
		'order'          => 'DEC'
		);

		$the_queryXXXX = new WP_Query($argsXXXX);
			while($the_queryXXXX->have_posts()) 
			$the_queryXXXX->the_post();
				$category = get_the_category();
				if(in_category('xxxx')){

					echo $the_queryXXX->post->ID;
					echo $the_queryXXX->post->post_title;
					echo $the_queryXXX->post->ID;
					echo $category[0]->cat_name;
					echo get_the_date('j F, Y');

				}
			wp_reset_postdata();
	?>

```

## POST_TYPE DE WORDPRESS CON PAGINACION
```php

	<?php 

	$arg = array(
		'post_type'     => 'slider',
		'post_per_page' => 3,
		'category_name' => 'slider',
		'orderby'       => 'title',
		'order'         => 'DEC',
		'paged'         => $paged
	);
	$mi_consulta = new WP_Query($arg);
	if ($mi_consulta->have_posts()) {
		while ($mi_consulta->have_posts()) {
			$mi_consulta->the_post();
			// Recupera el título de la publicación
			echo get_the_title().'<br>';
			// Recupera el nombre de la categoría
			// Referencia https://stackoverflow.com/questions/3037642/how-to-remove-list-from-php-the-category
			foreach((get_the_category()) as $category) {
				echo $category->cat_name.'<br>';
			}
			// Recupera la fecha de publicación
			echo get_the_date('d \d\e F \d\e Y');
			// Recupera el resumen de la publicación
			echo get_the_excerpt().'<br>';
			// Recupera el texto general de la publicación
			echo get_the_content().'<br>';
			// Recupera la imagen destacada primer parametro nombre de la funcion que realiza el crop de la imágen
			// Segundo parámetro array que contiene las clases de la imagen
			echo get_the_post_thumbnail( 'nombre_de_la_funcion_dimension_de_la_foto', array('class' => 'img-fluid')).'<br>';
			// Recupera el permalink
			echo get_the_permalink().'<br>';
		}
	echo the_pagination( $mi_consulta );
	}else{
		echo _e('Lo sentimos no existe Publicaciones');
	}
	?>

```

## LLAMADAS PARA OBTENER INFORMACIÓN GENERAL DEL SITIO
### URL DE REFERENCIA
[https://developer.wordpress.org/reference/functions/bloginfo/](https://developer.wordpress.org/reference/functions/bloginfo/)

~~~html

- Título del Sitio

	<?php bloginfo('name');?>

- Descripción de la página

	<?php bloginfo('description');?>

- Para recuperar la ruta hacia la hoja de estilo "style.css", de la Raíz.

  <?php bloginfo('stylesheet_url');?> 
  Esto devuelve la sigiente dirección: http://localhost/wp_inicio/content/themes/themes_query_01/style.css

- Para recuperar la ruta hacia cualquier carpeta.

  <?php bloginfo('template_url');?>
  Esto devuelve la ruta hacia un recurso que se aloja en una carpeta
  
  #Ejemplos:
  <img src="<?php bloginfo('template_url');?>/img/logo.png" alt="Logo">
  http://localhost/wp_inicio/content/themes/themes_01/img/logo.png
  
  <script src="<?php bloginfo('template_url');?>/js/jquery.js"></script>
  http://localhost/wp_inicio/content/themes/themes_query_01/js/jquery.js

~~~


## CREAR UN POST_TYPE
~~~html

add_action( 'init', 'codex_book_init' );

function codex_book_init() {
    $labels = array(
        'name'               => _x( 'Books', 'post type general name', 'your-plugin-textdomain' ),
        'singular_name'      => _x( 'Book', 'post type singular name', 'your-plugin-textdomain' ),
        'menu_name'          => _x( 'Books', 'admin menu', 'your-plugin-textdomain' ),
        'name_admin_bar'     => _x( 'Book', 'add new on admin bar', 'your-plugin-textdomain' ),
        'add_new'            => _x( 'Add New', 'book', 'your-plugin-textdomain' ),
        'add_new_item'       => __( 'Add New Book', 'your-plugin-textdomain' ),
        'new_item'           => __( 'New Book', 'your-plugin-textdomain' ),
        'edit_item'          => __( 'Edit Book', 'your-plugin-textdomain' ),
        'view_item'          => __( 'View Book', 'your-plugin-textdomain' ),
        'all_items'          => __( 'All Books', 'your-plugin-textdomain' ),
        'search_items'       => __( 'Search Books', 'your-plugin-textdomain' ),
        'parent_item_colon'  => __( 'Parent Books:', 'your-plugin-textdomain' ),
        'not_found'          => __( 'No books found.', 'your-plugin-textdomain' ),
        'not_found_in_trash' => __( 'No books found in Trash.', 'your-plugin-textdomain' )
    );

    $args = array(
        'labels'             => $labels,
        'description'        => __( 'Description.', 'your-plugin-textdomain' ),
        'public'             => true,
        'publicly_queryable' => true,
        'show_ui'            => true,
        'show_in_menu'       => true,
        'query_var'          => true,
        'rewrite'            => array( 'slug' => 'book' ),
        'capability_type'    => 'page',
        'has_archive'        => true,
        'hierarchical'       => false,
        'menu_position'      => null,
        'supports'           => array('title','editor','author','thumbnail','excerpt','category'),
        'taxonomies'         => array( 'category' ),
    );

    register_post_type( 'book', $args );
}
~~~

# DIFERENCIA ENTRE WP_PAGE_MENU Y WP_NAV_MENU
En WordPress, tanto wp_nav_menu() como wp_page_menu() son funciones que se utilizan para mostrar menús de navegación en un tema, pero tienen diferencias significativas en cuanto a su uso y funcionalidad:

1. wp_nav_menu():
Funcionalidad: Se utiliza para mostrar un menú de navegación personalizado. Este menú se gestiona desde el área de administración de WordPress, específicamente en "Apariencia" > "Menús".
Flexibilidad: Es muy flexible, ya que permite crear menús personalizados que pueden incluir enlaces a páginas, categorías, enlaces personalizados, y más.

Soporte para temas: Muchos temas de WordPress están diseñados para utilizar wp_nav_menu(), y suelen tener ubicaciones de menú específicas que pueden ser gestionadas a través del personalizador de WordPress.
Opciones de personalización: Permite utilizar una serie de parámetros para personalizar la salida del menú, como contenedores, clases CSS, y estructuras de lista. Además, es compatible con los walker classes, lo que permite personalizar cómo se renderiza el HTML del menú.

2. wp_page_menu():
Funcionalidad: Se utiliza para mostrar un menú basado en las páginas publicadas en el sitio. Este menú se genera automáticamente, sin necesidad de crear uno manualmente en el área de administración.
Automático: Es útil cuando no hay un menú personalizado creado en WordPress. En ausencia de un menú personalizado, wp_page_menu() lista automáticamente todas las páginas en el sitio.

Uso limitado: Está más limitado en términos de personalización en comparación con wp_nav_menu(). Generalmente, muestra una lista simple de páginas con opciones básicas de personalización como incluir un enlace al inicio (home) o definir clases CSS.
Backwards Compatibility: En temas más antiguos, esta función era comúnmente utilizada antes de la introducción de menús personalizados en WordPress 3.0.

### En resumen:
wp_nav_menu() es la opción preferida cuando se quiere un control total sobre la estructura y contenido del menú de navegación, utilizando la interfaz de administración de menús de WordPress.

wp_page_menu() es una solución más simple y automática que se basa en las páginas publicadas, útil cuando no se necesita un menú personalizado.

Si estás creando un tema o personalizando uno existente y quieres ofrecer la máxima flexibilidad a los usuarios, wp_nav_menu() es generalmente la mejor opción.

## RECUPERAR LOS WP_PAGE_MENU EN EL MENU DE NAVEGACION
```PHP

	<?php wp_page_menu(
		array(
			// Mostrar un enlace a la página de inicio. Puede ser 'true', 'false' o un texto personalizado.
			'show_home'   => true,  
			// Clase CSS a aplicar al contenedor del menú. 
			'menu_class'  => 'menu', 
			// IDs de las páginas a incluir en el menú, separados por comas.
			'include'     => '',  
			// IDs de las páginas a excluir del menú, separados por comas.   
			'exclude'     => '',    
			// Si se establece en 'true', se imprime el menú; si es 'false', se devuelve como una cadena. 
			'echo'        => true,
			// Texto para poner antes de cada enlace.
			'link_before' => '',  
			// Texto para poner después de cada enlace.   
			'link_after'  => '', 
			 // Niveles de anidación de páginas a mostrar. 0 significa sin límite.    
			'depth'       => 0,     
			// Columna o columnas por las que se ordenarán las páginas. Ejemplo: 'menu_order' o 'post_title'.
			'sort_column' => 'menu_order, post_title', 
			// Clase Walker personalizada para el menú.
			'walker'      => ''      
		)
	)
	;?>

```

## RECUPERAR LOS WP_NAV_MENU EN EL MENU DE NAVEGACION
```php
	<?php

		wp_nav_menu( array(
			'theme_location' => 'primary',   // Ubicación del menú registrado en functions.php
			'menu'           => '',          // Nombre, slug o ID del menú a mostrar. Si está vacío, se utilizará la ubicación.
			'container'      => 'div',       // Etiqueta HTML que contendrá el menú. Puede ser 'div', 'nav', 'false', etc.
			'container_class'=> 'menu-container', // Clase CSS del contenedor.
			'container_id'   => '',          // ID del contenedor.
			'menu_class'     => 'menu',      // Clase CSS para las <ul> del menú.
			'menu_id'        => '',          // ID para las <ul> del menú.
			'echo'           => true,        // Si es 'true', se imprime el menú. Si es 'false', se devuelve como una cadena.
			'fallback_cb'    => 'wp_page_menu', // Callback a ejecutar si no existe un menú.
			'before'         => '',          // Texto a añadir antes de cada enlace del menú.
			'after'          => '',          // Texto a añadir después de cada enlace del menú.
			'link_before'    => '',          // Texto a añadir antes del texto de cada enlace.
			'link_after'     => '',          // Texto a añadir después del texto de cada enlace.
			'items_wrap'     => '<ul id="%1$s" class="%2$s">%3$s</ul>', // Estructura HTML para envolver los elementos del menú.
			'depth'          => 0,           // Controla cuántos niveles de anidación se mostrarán. 0 significa sin límite.
			'walker'         => '',          // Clase Walker personalizada para tener control total sobre la salida del HTML.
		) );
		?>


```
## MODO DEBUG PARA PODER IDENTIFICAR ERRORES
### URL DE REFERENCIA
[https://wordpress.org/support/article/debugging-in-wordpress/](https://wordpress.org/support/article/debugging-in-wordpress/)

```PHP

	<?php

	//Se activa en el archivo wp-config.php
	define('WP_DEBUG', true);
	
	//Activa el archivo debug.log en wp-content, este archivo contendra los errores de escritura del código.
	define('WP_DEBUG_LOG', true);

	//Oculta el mensaje de error
	define('WP_DEBUG_DISPLAY', false);


	;?>

```


</section>
