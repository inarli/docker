FROM php:7.3-fpm
MAINTAINER ilkaynarli@gmail.com

RUN apt-get update

# install locale
RUN apt-get install --yes zlib1g-dev libicu-dev g++ \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl

# install pdo and pdo_pgsql
RUN apt-get install --yes libpq-dev \
    && docker-php-ext-configure pdo \
    && docker-php-ext-install pdo \
    && docker-php-ext-configure pdo_pgsql \
    && docker-php-ext-install pdo_pgsql

# install gd and imagick
RUN apt-get install --yes libpng-dev \
    && docker-php-ext-install gd \
    && docker-php-ext-configure gd \
    && apt-get install --yes imagemagick \
    && apt-get install --yes libmagickwand-dev \
    && pecl install imagick \
    && docker-php-ext-enable imagick

# install redis
RUN pecl install redis \
    && docker-php-ext-enable redis
