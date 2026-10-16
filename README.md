# Práctica: servidor Nginx con Docker Compose

Esta práctica ejecuta un servidor web Nginx en un contenedor y publica una página **Hola mundo** desde un directorio local.

## Requisitos

- Docker Desktop con Docker Compose v2.
- Git.

## Estructura

```text
.
├── docker-compose.yml
└── src/
    └── index.html
```

## Pasos de la práctica

### 1. Crear la página web

El archivo `src/index.html` contiene el mensaje **¡Hola mundo!**.

### 2. Configurar Docker Compose

El servicio usa la imagen `nginx:alpine`, publica el puerto `8080` y monta `./src` en el directorio web de Nginx:

```yaml
volumes:
  - ./src:/usr/share/nginx/html:ro
```

### 3. Ejecutar y verificar

Desde la raíz del proyecto:

```powershell
docker compose up -d
docker compose ps
```

Abrir <http://localhost:8080> y comprobar que aparezca **¡Hola mundo!**.

También se puede verificar desde PowerShell:

```powershell
(Invoke-WebRequest http://localhost:8080).StatusCode
```

El resultado esperado es `200`.

Para detener y eliminar el contenedor:

```powershell
docker compose down
```

### 4. Publicar en GitHub

```powershell
git init
git add .
git commit -m "Crear servidor Nginx con Docker Compose"
git branch -M main
git remote add origin https://github.com/osenrey-code/practica-nginx-docker-compose.git
git push -u origin main
```

## Resultado esperado

- El contenedor `practica-nginx` aparece en ejecución.
- <http://localhost:8080> responde con estado HTTP `200`.
- La página muestra **¡Hola mundo!**.
- El repositorio público contiene `docker-compose.yml`, `src/index.html` y este `README.md`.

## Verificación realizada

La práctica fue ejecutada y comprobada en Windows con WSL 2:

- Docker Engine `29.8.2` y Docker Compose `v5.6.0`.
- Configuración validada con `docker compose config`.
- Contenedor `practica-nginx` en estado `Up`.
- Puerto publicado: `0.0.0.0:8080->80/tcp`.
- `./src` montado en `/usr/share/nginx/html` en modo de solo lectura.
- <http://localhost:8080> respondió con estado HTTP `200` mediante `nginx/1.31.7`.
- Título, encabezado **¡Hola mundo!** y mensaje de Docker Compose comprobados.
