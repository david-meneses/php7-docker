# Docker Compose file for a PHP 7.4 Apache server with Xdebug and Composer

FROM php:7.4-apache
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update -y
RUN apt-get upgrade -y

RUN apt-get install -y libpng-dev 
RUN apt-get install -y libzip-dev
RUN apt-get install -y curl
RUN apt-get install -y zip unzip 
RUN apt-get install -y wget
RUN apt-get install -y cron
RUN apt-get install -y libxml2-dev

RUN docker-php-ext-install zip
RUN docker-php-ext-install gd
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN docker-php-ext-install xml
RUN docker-php-ext-install xmlrpc

# Install Xdebug 3.1.6
RUN pecl install xdebug-3.1.6 \
    && docker-php-ext-enable xdebug

# Configure Xdebug
COPY php.ini /usr/local/etc/php/php.ini

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

#COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

RUN a2enmod rewrite

ENV PHP_FPM_CLEAR_ENV=no
