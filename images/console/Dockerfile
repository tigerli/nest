FROM php:7.1
MAINTAINER lihu <tinylihu@163.com>

RUN apt-get update && apt-get install -y git curl libfreetype6-dev libzip-dev \
 && rm -rf /var/lib/apt/lists/* \
 && pecl install zip \
 && docker-php-ext-enable zip

RUN git config --global user.name 'lihu' \
 && git config --global user.email 'tinylihu@163.com'

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
 && php -r "if (hash_file('sha384', 'composer-setup.php') === '48e3236262b34d30969dca3c37281b3b4bbe3221bda826ac6a9a62d6444cdb0dcd0615698a5cbe587c3f0fe57a54d8f5') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
 && php composer-setup.php \
 && php -r "unlink('composer-setup.php');" \
 && mv composer.phar /usr/local/bin/composer \
 && echo 'export PATH="$PATH:$HOME/.composer/vendor/bin"' >> ~/.bashrc \
 && . ~/.bashrc \
 && composer config -g repo.packagist composer https://packagist.phpcomposer.com 

# # 定位到工作目录
# WORKDIR /mnt/www