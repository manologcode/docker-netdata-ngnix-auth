FROM nginx

RUN apt-get update -y \
    && apt-get install -y \
        apache2-utils \
    && rm -rf /var/lib/apt/lists/*

ENV FORWARD_PORT=19999

WORKDIR /opt

#RUN apk add --no-cache gettext

COPY ./nginx/auth.conf ./nginx/auth.htpasswd ./nginx/launch.sh /opt

RUN chmod 0755 /opt/launch.sh

EXPOSE 19999

CMD ["/opt/launch.sh"]
