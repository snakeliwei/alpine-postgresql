FROM alpine:3.8
LABEL maintainer="lyndon <snakeliwei@gmail.com>"

RUN sed -i 's/postgres:x:70:/postgres:x:2000:/g' /etc/group && \
    sed -i 's/postgres:x:70:70/postgres:x:2000:2000/g' /etc/passwd && \
    apk add --no-cache --update 'su-exec>=0.2' tzdata postgresql postgresql-contrib && \
    mkdir /docker-entrypoint-initdb.d && \
    mkdir -p /run/postgresql/ && \
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
