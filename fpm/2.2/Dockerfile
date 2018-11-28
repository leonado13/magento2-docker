FROM php:7.1-fpm

MAINTAINER "Tuan Nguyen <ng.nhat.tuan@gmail.com>"

ENV MAGENTO_VERSION 2.2.6
ENV WORKING_DIR /var/www/html

RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer

RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libmcrypt-dev \
    libicu-dev \
    libxslt-dev \
    mcrypt \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install calendar \
    && docker-php-ext-install exif \
    && docker-php-ext-install gettext \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd \
    && docker-php-ext-install intl \
    && docker-php-ext-install xsl \
    && docker-php-ext-install zip \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install soap \
    && docker-php-ext-install mcrypt

RUN chsh -s /bin/bash www-data

RUN chown -R www-data:www-data /var/www

RUN echo "memory_limit=2048M" > /usr/local/etc/php/conf.d/memory-limit.ini

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR $WORKING_DIR
