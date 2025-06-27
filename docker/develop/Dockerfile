FROM dunglas/frankenphp:1.5.0-php8.4.5-alpine

RUN apk add --update nodejs npm && \
    npm install -g chokidar && \
    install-php-extensions \
    pcntl \
    redis \
    bcmath \
    xdebug \
    pdo \
    pdo_mysql && \
    echo 'memory_limit = 256M' > /usr/local/etc/php/conf.d/memory_limit.ini

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/

ENV XDEBUG_MODE=off

ENTRYPOINT ["php", "artisan", "octane:frankenphp", "--watch", "--poll", "--host=127.0.0.1", "--port=80"]
