FROM php:8.1-apache-bullseye

# apt-get install
RUN apt-get update \
&& apt-get install -y \
libwebp-dev \
libpng-dev \
libjpeg62-turbo-dev \
libfreetype6-dev \
libzip-dev \
libicu-dev \
git \
locales locales-all

# php extentions
RUN docker-php-ext-configure gd --with-webp=/usr/include/ --with-jpeg=/usr/include/ --with-freetype=/usr/include/ \
&& docker-php-ext-install gd \
&& docker-php-ext-install pdo_mysql \
&& docker-php-ext-install mysqli \
&& docker-php-ext-install zip

# php ini
RUN cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini
COPY docker/php-custom.ini /usr/local/etc/php/conf.d/php-custom.ini

# apache
RUN a2enmod rewrite

# processwire
RUN git clone https://github.com/processwire/processwire.git -b master /var/www/html
WORKDIR /var/www/html
RUN rm -rf .git site-*
RUN mv htaccess.txt .htaccess

# cleanup
RUN apt-get clean

EXPOSE 80

# apache2 fix: Could not reliably determine the server's fully qualified domain name
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf