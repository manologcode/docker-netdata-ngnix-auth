# netdata authentication with nginx

este repositorio es contiene un contenedor nginx con Restricting Access with HTTP Basic Authentication para exponer el contendor netdata con contraseña

netdata es un proyecto de sofware libre para monitorizar servidors que corre sobre docker. la direccion de proyecto https://www.netdata.cloud/

construir la imagne de netdata_auth

        docker build -t manologcode/netdata_auth ./nginx

para correrlo clonar el copiar el docker-compose cambiar los parametros de usuario y contrase;a y correr

docker-compose up -d
