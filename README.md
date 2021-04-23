# netdata authentication with nginx

Este repositorio es contiene un contenedor nginx con Restricting Access with HTTP Basic Authentication para exponer el contendor netdata con contraseña

netdata es un proyecto de sofware libre para monitorizar servidors que corre sobre docker. la direccion de proyecto https://www.netdata.cloud/

Para correrlo clonar el repositoro o el copiar el docker-compose cambiar los parametros de usuario y contraseña y correr

        docker-compose up -d

corre en el servidor sobre el puerto 19999

        http://51.XXX.XXX.XXX:19999/