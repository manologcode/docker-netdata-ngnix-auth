# netdata authentication with nginx

Este repositorio es contiene un contenedor nginx con Restricting Access with HTTP Basic Authentication para exponer el contenedor Netdata con contraseña

Netdata es un proyecto de software libre para monitorizar servidores que corre sobre docker. la dirección de proyecto https://www.netdata.cloud/

copiar el docker-compose.yml cambiar los parámetros de usuario y contraseña y correr

    curl https://raw.githubusercontent.com/manologcode/docker-netdata-ngnix-auth/master/docker-compose.yml >> docker-compose.yml

    docker-compose up -d

corre en el servidor sobre el puerto 19999 

        http://51.XXX.XXX.XXX:19999/

integrar en el contenedor nginx proxi

version: '3'
services:
  netdata:
    image: netdata/netdata
    container_name: netdata
    networks:
      - net_netdata
    expose:
      - 19999
    restart: unless-stopped
    cap_add:
      - SYS_PTRACE
    security_opt:
      - apparmor:unconfined
    environment:
      - TELEGRAM_BOT_TOKEN=xxxxxxxxxxxxxxxxxxxxxxxxx 
      - TELEGRAM_CHAT_ID=XXXXXXXXXXX
    
    volumes:
      - netdata:/etc/netdata:ro
      - netdatalib:/var/lib/netdata
      - netdatacache:/var/cache/netdata
      - /etc/passwd:/host/etc/passwd:ro
      - /etc/group:/host/etc/group:ro
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
      - /etc/os-release:/host/etc/os-release:ro

  auth:
    image: manologcode/netdata_auth
    container_name: nginx-auth
    networks:
      - net_netdata
    ports:
      - 19999:19999
    links:
      - netdata
    environment:
      USER: "1234"
      PASS: "1234"

volumes:
  netdata:
  netdatalib:
  netdatacache:

networks:
  net_netdata:    

