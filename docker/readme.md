# Cómo usar

Para utilizar docker-compose, copia el archivo **template.docker-compose.yml** y renómbralo a **docker-compose.yml**.

Una vez que tenamos el archivo para docker-compose, lo editamos y agregamos los datos para nuestro contenedor.

## Campos a editar en _docker-compose.yml_:

container_name: Para indicar el nombre que tendrá el contenedor al crearse. Ejemplo:

```yaml
container_name: mi_contenedor_mysql
```

ports: Lista de puertos a usar. El siguiente ejemplo muestra como redireccionar a un puerto del anfitrión (host):

```yaml
ports:
    - "33060:3306" # puerto_anfitrion (tu pc):puerto_instancia (dentro de docker).
```

expose: Lista de puertos de la instancia que serán expuestos.

```yaml
expose:
    - "3306" # Puerto de la instancia.
```

environment: Variables de entorno para la creación del contenedor.

```yaml
environment:
    MYSQL_ROOT_PASSWORD: <contrasena_root> # Contraseña para el usuario "root".
    MYSQL_DATABASE: <nombre_bd> # "Nombre de la BD que será creada en el contenedor."
    MYSQL_USER: <usuario_bd> # Nombre del usuario que será creado y se le asignará permisos de acceso a la BD creada en el contenedor.
    MYSQL_PASSWORD: <contrasena_usuario_bd> # Contraseña para el usuario creado para la BD del contenedor.
```
