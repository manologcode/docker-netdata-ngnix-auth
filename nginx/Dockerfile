FROM nginx

RUN apt-get update -y \
    && apt-get install -y \
        apache2-utils \
    && rm -rf /var/lib/apt/lists/*

ENV FORWARD_PORT=19999

WORKDIR /opt

#RUN apk add --no-cache gettext

COPY auth.conf auth.htpasswd launch.sh ./

RUN chmod 0755 ./launch.sh

EXPOSE 19999

CMD ["./launch.sh"]
