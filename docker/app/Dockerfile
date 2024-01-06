FROM php:8.1-fpm-buster

ENV COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_HOME=/composer

COPY --from=composer:2.2 /usr/bin/composer /usr/bin/composer

RUN apt-get update \
    && apt-get install -y \
        libzip-dev \
        libpq-dev \
        libicu-dev \
        libonig-dev \
        git\
        unzip \
        vim && \
        apt-get clean && \
        rm -rf /var/lib/apt/lists/* && \
        docker-php-ext-install intl pdo_pgsql zip bcmath

COPY ./php.ini /usr/local/etc/php/php.ini

WORKDIR /data

