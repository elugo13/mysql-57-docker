# MySQL Docker Container

Repositorio para crear un contenedor de MySQL en Docker.

## Crear el contenedor

**Pre-requisitos**:

* docker
* docker-compose

En una terminal abrir la ubicación del archivo **docker-compose.yml** y ejecutar

    docker-compose up -d

_Salida_:

    Creating network "mysql57_mysql_host" with driver "bridge"
    Creating volume "mysql57_schemas" with default driver
    Pulling mysql (mysql:5.7)...
    5.7: Pulling from library/mysql
    69692152171a: Pull complete
    1651b0be3df3: Pull complete
    951da7386bc8: Pull complete
    0f86c95aa242: Pull complete
    37ba2d8bd4fe: Pull complete
    6d278bb05e94: Pull complete
    497efbd93a3e: Pull complete
    a023ae82eef5: Pull complete
    e76c35f20ee7: Pull complete
    e887524d2ef9: Pull complete
    ccb65627e1c3: Pull complete
    Digest: sha256:a682e3c78fc5bd941e9db080b4796c75f69a28a8cad65677c23f7a9f18ba21fa
    Status: Downloaded newer image for mysql:5.7
    Creating mysql_test_db ... 
    Creating mysql_test_db ... done

## Conectarse a la instancia

Para poder conectarnos a la instancia, debemos obtener su **ip**. Para esto debemos ingresar al contenedor ejecutando esta instrucción:

    docker exec -it mysql_test_db bash

_Salida_:

    root@3d8904154034:/#

Una vez dentro del contenedor, ejecutamos:

    cat /etc/resolve.conf

_Salida_:

    search some.domain
    nameserver 127.0.0.11
    options ndots:0

Terminamos la sesión del contenedor presionando "ctrl+d"

Ahora hacemos ping a esta ip para comprobar si podemos alcanzarla:

    ping 127.0.0.11

_Salida_:

    PING 127.0.0.11 (127.0.0.11) 56(84) bytes of data.
    64 bytes from 127.0.0.11: icmp_seq=1 ttl=64 time=0.056 ms
    64 bytes from 127.0.0.11: icmp_seq=2 ttl=64 time=0.049 ms
    64 bytes from 127.0.0.11: icmp_seq=3 ttl=64 time=0.061 ms
    64 bytes from 127.0.0.11: icmp_seq=4 ttl=64 time=0.059 ms
    64 bytes from 127.0.0.11: icmp_seq=5 ttl=64 time=0.062 ms
    ^C
    --- 127.0.0.11 ping statistics ---
    5 packets transmitted, 5 received, 0% packet loss, time 4096ms
    rtt min/avg/max/mdev = 0.049/0.057/0.062/0.008 ms

**¡Listo!**

Ahora podrás conectarte usando el método que prefieras, por terminal (mysql-client o mysql-shell), por alguna herramienta con interfaz gráfica (MySQL Workbench, DBeaver Community...) o programáticamente con el lenguaje que prefieras (c#, python, java...).

### Ejemplo de conexión por terminal

**Pre-requisitos**:

* mysql-client

Ejecutar la siguiente instrucción:

    your-user@your-pc:~$ mysql -h 127.0.0.11 -P 33060 -u your_user

Se solicitará la contraseña del usuario. Ingrésala y presiona "Enter"

_Salida_:

    Welcome to the MySQL monitor.  Commands end with ; or \g.
    Your MySQL connection id is 3
    Server version: 5.7.34 MySQL Community Server (GPL)

    Copyright (c) 2000, 2021, Oracle and/or its affiliates.

    Oracle is a registered trademark of Oracle Corporation and/or its
    affiliates. Other names may be trademarks of their respective
    owners.

    Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

    mysql>

