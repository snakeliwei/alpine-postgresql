FROM alpine:edge
MAINTAINER lyndon <snakeliwei@gmail.com>

RUN apk add --no-cache --update 'su-exec>=0.2' tzdata postgresql && \
    mkdir /docker-entrypoint-initdb.d && \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    rm -rf /var/cache/apk/*

ENV LANG C.UTF-8
ENV PGDATA /var/lib/postgresql/data
VOLUME /var/lib/postgresql/data

COPY docker-entrypoint.sh /
RUN chmod +x /docker-entrypoint.sh

ENTRYPOINT ["/docker-entrypoint.sh"]

EXPOSE 5432
CMD ["postgres"]
