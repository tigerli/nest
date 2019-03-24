FROM php:7.0
MAINTAINER  lihu <tinylihu@163.com>

RUN apt-get update && apt-get install -y libjpeg-dev libpng-dev \
 && rm -rf /var/lib/apt/lists/* \
 && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
 && docker-php-ext-install gd pdo_mysql zip opcache

COPY ./config/php.ini /usr/local/etc/php/conf.d/
COPY ./config/opcache-recommended.ini /usr/local/etc/php/conf.d/