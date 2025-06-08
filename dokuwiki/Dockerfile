FROM alpine:3.18

RUN apk add --no-cache \
    php81 \
    php81-fpm \
    php81-opcache \
    php81-session \
    php81-gd \
    php81-xml \
    php81-zlib \
    nginx \
    supervisor \
    curl

WORKDIR /var/www/html

# Скачиваем и распаковываем DokuWiki (версия будет подставляться из CI)
ARG DOKUWIKI_VERSION
RUN curl -L "https://github.com/dokuwiki/dokuwiki/archive/refs/tags/release_stable_${DOKUWIKI_VERSION}.tar.gz" | tar -xz --strip-components=1

COPY dokuwiki/nginx.conf /etc/nginx/nginx.conf
COPY dokuwiki/supervisord.conf /etc/supervisord.conf

EXPOSE 80
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisord.conf"]