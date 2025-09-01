

# Curso de Introducción a WordPress

![Landing Blog Actualidad](screenshot.png)

## 📖 Introducción

WordPress es uno de los sistemas de gestión de contenidos (CMS) más utilizados en el mundo. Con él puedes crear desde un blog personal hasta un sitio web corporativo, una tienda en línea o incluso una plataforma educativa.  
Su éxito se debe a su **facilidad de uso**, **flexibilidad** y a la gran **comunidad de desarrolladores y diseñadores** que lo respaldan.  

Aprender WordPress es una excelente manera de iniciarse en el desarrollo web, ya que combina lo mejor de dos mundos:  
- Una interfaz amigable que permite administrar contenidos sin necesidad de saber programar.  
- La posibilidad de extender y personalizar cada detalle mediante **temas, plugins y código propio** (PHP, HTML, CSS y JavaScript).  

En este curso aprenderás los fundamentos básicos:  
- **Instalación en local** para practicar en tu propio computador.  
- **Creación de publicaciones y páginas** para organizar tu contenido.  
- **Uso de temas** para personalizar el aspecto visual.  
- **Integración de cabecera y pie de página** entendiendo hooks y encolamiento de scripts.  
- **Template parts** para reutilizar componentes.  
- **Creación de menús y navegación** para estructurar tu sitio.  

El objetivo es que, al finalizar, seas capaz de **instalar, personalizar y administrar un sitio web en WordPress**, conociendo tanto la parte visual como la lógica que hay detrás.

---

## Descarga de tutoriales
- [00- Archivos base para crear el tema](https://drive.google.com/file/d/1nKIVZ1lBb3hPMJkR9hJSn3jNBwU00tiS/view?usp=sharing)
- [01 - Introducción](https://drive.google.com/file/d/1tkf_ncYNcaDXSogAo0Kjnunzq82ShQOi/view?usp=sharing)
- [02 - Instalación WordPress Local](https://drive.google.com/file/d/1CUIFGbVc5XfvmUJ3B9maeC1kG7kmJcuY/view?usp=sharing)
- [03 - Creación de Post o Publicaciones](https://drive.google.com/file/d/1B7l4h1WG216BZ5NYMf2ox18b7yqZivFh/view?usp=sharing)
- [04 - Iniciando un Theme](https://drive.google.com/file/d/1wEFu-rTodftc5pABRphaKD0YsHPhDaOl/view?usp=sharing)
- [05 - Integrar Header, Footer, Hook y Encolamiento](https://drive.google.com/file/d/1viPRDG51d9QjT1IOhLuAPlzx7VxlIoGR/view?usp=sharing)
- [06 - Get Template Parts: Cómo obtener los Posts](https://drive.google.com/file/d/14xF0tkhZ-0Q9Iuyj7jvnFPrmzsf_Pw6S/view?usp=sharing)
- [07 - Creando el Nav](https://drive.google.com/file/d/1S8uLjnCNhtDIDddAj4-G4D-qrFXrHyYZ/view?usp=sharing)
- [08 - Creando Header, Footer y Single Page](https://drive.google.com/file/d/1ydmE2Rs2BOEwFG19M7GyObbuDY6BYCII/view?usp=sharing)

---

### Para crear un Theme desde cero, se necesita como minimo:
~~~

	-wp-content/themes/mi_tema
	|
	|– index.php  
	|– style.css
	|– screenshot.png
	|– function.php

~~~
---

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
---

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

---

### ENCOLAMIENTO DE ARCHIVOS CSS Y JS MINIMO VIABLE

#### function.php

```php

	function my_theme_setup() {
		// Soporte para imágenes destacadas
		add_theme_support('post-thumbnails');
		
		// Soporte para título dinámico
		add_theme_support('title-tag');
		
		// Registro de menú
		register_nav_menus(array(
			'primary' => __('Primary Menu', 'my-theme'),
			'sidebar' => __('Sidebar Menu', 'my-theme'),
		));
	}
	add_action('after_setup_theme', 'my_theme_setup');

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

	
	function formato_personalizado_fecha_latino($the_date, $d) {
    	return date_i18n('d/m/Y', strtotime($the_date));
	}

	add_filter('get_the_date', 'formato_personalizado_fecha_latino', 10, 2);


	function agregar_favicon() {
		// Obtener la URL del tema
		$favicon_url = get_template_directory_uri() . '/assets/img/icon.svg';

		// Imprimir la etiqueta HTML para el favicon en la cabecera
		echo '<link rel="shortcut icon" href="' . esc_url($favicon_url) . '" />';
	}

	// Hook para añadir el favicon en el head del tema
	add_action('wp_head', 'agregar_favicon');

```