# Docker Angular con Apache

Imagen Docker que ejecuta un servidor web Apache sirviendo una aplicación Angular sobre Debian.

## Descripción

Este proyecto crea una imagen Docker que:
- Usa Debian como imagen base
- Instala Apache como servidor web
- Instala Node.js y npm
- Instala Angular CLI globalmente
- Crea y sirve una aplicación Angular con el mensaje "¡Bienvenido a mi servidor Docker con Angular!"

## Requisitos

- Docker instalado (versión 20.10 o superior)
- Docker Hub cuenta (para publicar la imagen)
- Git (para clonar el repositorio)

## Instrucciones de uso

### 1. Clonar el repositorio

```bash
git clone https://github.com/joseabad985/EXAMÉNINTERCICLO65
cd EXAMÉNINTERCICLO65
```

### 2. Construir la imagen Docker

```bash
docker build -t angular-apache-debian .
```

### 3. Ejecutar el contenedor

```bash
docker run -d -p 80:80 --name mi-servidor-angular angular-apache-debian
```

### 4. Acceder a la aplicación

Abrir el navegador en: http://localhost

Verás la aplicación Angular con el mensaje "¡Bienvenido a mi servidor Docker con Angular!"

### 5. Detener y eliminar el contenedor

```bash
docker stop mi-servidor-angular
docker rm mi-servidor-angular
```

## Volúmenes

Para desarrollo, puedes montar un volumen para modificar el código sin reconstruir:

```bash
docker run -d -p 80:80 -v $(pwd)/app:/var/www/html --name mi-servidor-angular angular-apache-debian
```

## Estructura del proyecto

```
.
├── Dockerfile          # Configuración de la imagen Docker
├── README.md          # Este archivo
└── .dockerignore      # Archivos a ignorar por Docker (opcional)
```

## Configuración del Dockerfile

El Dockerfile realiza las siguientes acciones:

1. Parte de la imagen `debian:latest`
2. Instala Apache2
3. Instala Node.js y npm
4. Instala Angular CLI globalmente
5. Crea una aplicación Angular
6. Modifica el mensaje de bienvenida
7. Construye la aplicación para producción
8. Configura Apache para servir la aplicación
9. Expone el puerto 80

## Publicar en Docker Hub

```bash
# Hacer login en Docker Hub
docker login

# Etiquetar la imagen
docker tag angular-apache-debian joseabad985/angular-apache-debian:latest

# Subir la imagen
docker push joseabad985/angular-apache-debian:latest
```

## Descargar desde Docker Hub

```bash
docker pull joseabad985/angular-apache-debian:latest
docker run -d -p 80:80 --name mi-servidor-angular joseabad985/angular-apache-debian:latest
```

## Autor

José Abad

## Licencia

Este proyecto es parte de una práctica académica.