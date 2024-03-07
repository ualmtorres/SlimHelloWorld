# Creación de una API REST con Slim Framework

## Introducción

Slim es un micro framework PHP que nos permite crear aplicaciones web y APIs REST de forma rápida y sencilla. En este tutorial vamos a ver cómo crear una API REST con Slim Framework.

## Instalación

Aquí usaremos una instalación con Docker Composer, pero también se puede instalar Slim Framework de forma manual. En nuestro caso, se crearán dos contenedores, uno para Slim y otro para Nginx. No usaremos las imágenes oficiales de PHP y Nginx, sino que crearemos nuestras propias imágenes con nuestras configuraciones. La configuración de Nginx se hará con un archivo de configuración (`default.conf`) personalizado. La configuración de Slim se hará mediante un archivo `Dockerfile`.

Usaremos la siguiente estructura de directorios:

```
.
├── composer.json
├── docker-compose.yml
├── nginx
│   └── default.conf
├── php
│   └── Dockerfile
└── public
    └── index.php
```

### Dockerfile para Slim

<script src="https://gist.github.com/ualmtorres/807d30e835c4c749a83c164b36694cb7.js"></script>

Almacenamos este archivo en la carpeta `php` de nuestro proyecto.

### Archivo de configuración de Nginx

<script src="https://gist.github.com/ualmtorres/cb4be3716b944bd3a841eff6fd8b654e.js"></script>

Almacenamos este archivo en la carpeta `nginx` de nuestro proyecto.

### Docker Compose

<script src="https://gist.github.com/ualmtorres/70c5a58d5d0b0bfed0bf87ee2d2df594.js"></script>

Almacenamos este archivo en la raíz de nuestro proyecto.

### Ejecución del entorno

Para ejecutar nuestra aplicación, ejecutamos el siguiente comando:

```bash
docker-compose up -d
```

Para configurar Slim, necesitamos un archivo `composer.json` con las dependencias necesarias. En nuestro caso, necesitamos Slim y el adaptador de Slim para PSR-7. El archivo `composer.json` es el siguiente:

<script src="https://gist.github.com/ualmtorres/140906bb280f62b4cab14e3ff5a6756b.js"></script>

### Instalación de las dependencias del proyecto

Para instalar las dependencias del proyecto, ejecutamos el siguiente comando:

```bash
docker-compose exec php composer install
```

## Creación de una API REST

Para crear una API REST con Slim, necesitamos un archivo `index.php` con el siguiente contenido:

<script src="https://gist.github.com/ualmtorres/15125d3ca5383d5551bc9ff733dd0d8e.js"></script>

Si todo ha ido bien, podemos acceder a nuestra aplicación en `http://localhost:8080`. Si accedemos a `http://localhost`, deberíamos ver el mensaje `Hello from Slim`.

