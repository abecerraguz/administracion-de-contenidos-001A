# Semana 05 - Ejercicios: Publicando el Blog en cPanel

**Proyecto integrador:** Blog Actualidad — Fase 5 de 8
**Tutoriales de referencia:** `12 - Publicación de WordPress desde localhost a cPanel`

> Esta semana el tema deja el entorno local y se despliega en un servidor real. El blog debe quedar accesible desde internet.

---

## Ejercicio 1 — Exportar la base de datos local

**Descripción:** Generar el respaldo de la base de datos MySQL para migrarla al servidor.

**Instrucciones:**

1. Abre **phpMyAdmin** en tu entorno local (`http://localhost/phpmyadmin`).
2. Selecciona la base de datos de tu instalación `blog-actualidad`.
3. Ve a la pestaña **Exportar** y selecciona el formato **SQL**. Descarga el archivo `.sql`.
4. Abre el archivo `.sql` exportado en un editor de texto y localiza la línea que dice `siteurl` y `home`. Anota los valores que tienen actualmente (URL local).

---

## Ejercicio 2 — Crear base de datos y usuario en cPanel

**Descripción:** Configurar la base de datos remota donde vivirá el sitio.

**Instrucciones:**

1. Ingresa a **cPanel** del servidor proporcionado por el docente.
2. Ve a **Bases de datos MySQL** y crea una nueva base de datos (ej. `user_blogact`).
3. Crea un **usuario MySQL** con contraseña segura.
4. Asigna el usuario a la base de datos con **todos los privilegios**.
5. En **phpMyAdmin** de cPanel importa el archivo `.sql` exportado en el ejercicio anterior.

---

## Ejercicio 3 — Subir los archivos y configurar wp-config.php

**Descripción:** Subir el tema y actualizar la configuración de WordPress para el servidor remoto.

**Instrucciones:**

1. Conecta al servidor vía **FTP/SFTP** (usa FileZilla u otro cliente).
2. Sube la carpeta completa de tu instalación WordPress al directorio `public_html` (o la carpeta asignada).
3. Abre `wp-config.php` y actualiza las siguientes constantes con los datos de cPanel:

```php
define( 'DB_NAME',     'user_blogact' );   // nombre de la BD en cPanel
define( 'DB_USER',     'user_mysql' );     // usuario MySQL de cPanel
define( 'DB_PASSWORD', 'tu_password' );   // contraseña del usuario
define( 'DB_HOST',     'localhost' );     // generalmente localhost en cPanel
```

4. En phpMyAdmin de cPanel, actualiza los valores `siteurl` y `home` en la tabla `wp_options` con la URL del servidor remoto.
5. Accede al sitio desde el navegador y verifica que carga correctamente.

---

## Preguntas de Repaso

1. ¿Por qué hay que actualizar `siteurl` y `home` en la tabla `wp_options` al migrar?
2. ¿Qué información contiene `wp-config.php`? ¿Por qué nunca debe subirse a un repositorio público?
3. ¿Qué es FTP y para qué se usa en este proceso?
4. ¿Qué diferencia hay entre la base de datos local y la remota?
