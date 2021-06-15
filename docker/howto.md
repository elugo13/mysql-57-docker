# Cómo usar

Para utilizar docker-compose, copia el archivo **template.docker-compose.yml** y renómbralo a **docker-compose.yml**.

Una vez que tenamos el archivo para docker-compose, lo editamos y agregamos los datos para nuestro contenedor.

_docker-compose.yml_
```yaml
version: '3.3'
services:
    mysql:
        image: mysql:5.7
        container_name: <nombre_contenedor>
        command: --default-authentication-plugin=mysql_native_password
        restart: always
        ports:
            - "33060:3306"
        expose:
            - "3306"
        environment:
            MYSQL_ROOT_PASSWORD: <contrasena_root>
            MYSQL_DATABASE: <nombre_bd>
            MYSQL_USER: <usuario_bd>
            MYSQL_PASSWORD: <contrasena_usuario_bd>
        volumes:
            - schemas:/var/lib/mysql
        networks:
            mysql_host:
                aliases:
                    - mysql_net
networks:
    mysql_host:
        driver: bridge
volumes:
    schemas:
```
