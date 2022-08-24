# Docker para desarrollo en Go y Postgres

Este contenedor instala lo necesario para correr un programa en Go usando contendores de Docker.

El contenedor es independiente del código, es decir, que es necesario contar con un repositorio descargado o clonado antes de poder usar el contendor.

| Componente      | Versión      |
|-----------------|-------------:|
|Docker desktop   | 2.5 (stable) |
|Engine           |19.03         |
|Compose          |1.27          |
|Kubernetes       |1.19          |
|Notary           |0.6           |
|Credential Helper|0.6           |
|Snyk             |1.424         |

Para la instalación y puesta en marcha:
[https://docs.docker.com/desktop/](https://docs.docker.com/desktop/)

## Estructura de directorio

En cualquier directorio donde el usuario tenga acceso, crear un directorio de trabajo, por ejemplo:

| S.O. | Ruta                     | Directorio |
|------|--------------------------|------------|
| Mac  | `~/Documents/Go`         | `proyecto`  |
| Win  | `C:\Users\juan\Documents`| `proyecto`  |

Crear los siguientes directorios:

- .devcontainer (invisible)
- bin
- pkg
- src

Dentro de `src` clonar o descargar el repositorio de `proyecto`.

Copiar este repo del contenedor dentro de el directorio `.devcontainer`

Para correr el contenedor en VS Code:

* Instalar la extensión [`Remote - Containers`](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
* Usar el comando `Remote-Containers: Open Folder in Container...`

## Versiones de software instaladas

|           |Versión         |
|-----------|---------------:|
|Sistema    |Debian 10 Buster|
|Go         |1.15.6          |
|Postgres   |13.1            |

## Extensiones instaladas de VS Code

|Nombre     |Descripción                    |
|-----------|-------------------------------|
|Docker     |gestión de contenedores        |
|Go         |soporte de lenguage            |
|PostgeSQL  |conexión y ejecución de queries|
|Preview    |visualizar archivos .md        |
|REST Client|ejecución de peticiones REST   |
|uppercase  |convertir a todo mayúsculas    |
|vscode-json|soporte para archivos json     |
|DotENV     |soporte para archivos .env     |

Para agregar más extensiones modificar en el archivo `devcontainer.json` la sección `extensions`.

## Puertos disponibles

|||
|---|---|
| Api      | locahost:3000  |
| Postgres | localhost:5432 |

## Base de datos

Después de haber lanzado el contenedor, si es necesario cargar datos a la bd llamada `postgres` (creada por defecto) con el usuario `postgres`, donde `dump.sql` es el archivo a cargar:

`psql postgres < dump.sql -h localhost -U postgres`

Para cambiar el nombre de la base de datos, así como el nombre de usuario y contraseña creados por defecto, editar estos datos en el archivo `devcontainer.json` en la sección `settings`.`sqltools.connections` y repetir los mismos valores en `docker-compose.yml` en la sección `db`.`environment`.
