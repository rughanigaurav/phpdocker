FROM php:8.1-apache

# CONFIGURE PHP
RUN ln -s /usr/local/bin/php /usr/bin/php
RUN apt-get update && apt-get install -y libpq-dev libmcrypt-dev libzip-dev libssl-dev unzip git libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        && docker-php-ext-install zip pdo bcmath \
        && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
        && docker-php-ext-install -j$(nproc) gd

RUN pecl install mongodb && docker-php-ext-enable mongodb

#RUN echo 'deb http://apt.vandenbrand.org/debian testing main' | tee /etc/apt/sources.list.d/#rabbitmq-cli-consumer.list > /dev/null

#ADD apt.vandenbrand.org.gpg.key /tmp
#RUN apt-key add /tmp/apt.vandenbrand.org.gpg.key && apt-get update && apt-get install -y rabbitmq-cli-consumer

RUN apt-get update && apt-get install -y libmagickwand-dev --no-install-recommends && rm -rf /var/lib/apt/lists/*
RUN pecl install imagick && docker-php-ext-enable imagick

RUN apt-get update && apt-get install -y zlib1g-dev libicu-dev g++
RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl
RUN docker-php-ext-install pdo pdo_mysql
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install simplexml && docker-php-ext-enable simplexml
RUN docker-php-ext-install dom

RUN curl -sL https://deb.nodesource.com/setup_16.x | bash -
RUN apt-get install -y nodejs

# RUN pecl install xdebug
# SETUP APACHE
RUN a2enmod rewrite
RUN a2enmod ssl
RUN a2enmod headers
RUN docker-php-ext-install sockets
RUN docker-php-ext-install exif

# Use the default production configuration
ADD php.ini /etc/php.ini
RUN mv /etc/php.ini "$PHP_INI_DIR/php.ini"

ADD vhost.conf /etc/apache2/sites-available/000-default.conf


WORKDIR /app

EXPOSE 80