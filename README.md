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
git remote add origin URL_DEL_REPOSITORIO
git push -u origin main
```

## Resultado esperado

- El contenedor `practica-nginx` aparece en ejecución.
- <http://localhost:8080> responde con estado HTTP `200`.
- La página muestra **¡Hola mundo!**.
- El repositorio público contiene `docker-compose.yml`, `src/index.html` y este `README.md`.
