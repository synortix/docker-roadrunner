
# syntax:docker/dockerfile:1

FROM alpine:3.8

RUN apk --no-cache add \
    php7 php7-cgi php7-ctype php7-json php7-dom php7-zip php7-zip php7-gd \
    php7-curl php7-mbstring php7-redis php7-mcrypt php7-iconv php7-posix php7-pdo_mysql php7-tokenizer php7-simplexml php7-session \
    php7-xml php7-sockets php7-openssl php7-fileinfo php7-ldap php7-exif php7-pcntl php7-xmlwriter php7-phar php7-zlib \
    php7-intl

RUN apk --no-cache add wget \
    && wget https://github.com/spiral/roadrunner/releases/download/v1.3.2/roadrunner-1.3.2-linux-amd64.tar.gz \
    && apk del --purge wget \
    && tar -xvzf roadrunner-1.3.2-linux-amd64.tar.gz \
    && mv roadrunner-1.3.2-linux-amd64 roadrunner \
    && rm roadrunner-1.3.2-linux-amd64.tar.gz

ENTRYPOINT ["/roadrunner/rr"]
