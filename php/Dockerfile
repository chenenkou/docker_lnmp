FROM php:7.1.18-fpm

COPY php.ini /usr/local/etc/php/php.ini

RUN docker-php-ext-install pdo_mysql

# install mongodb ext
RUN pecl install mongodb \
    && docker-php-ext-enable mongodb

# install redis ext
RUN pecl install -o -f redis \
	&&  rm -rf /tmp/pear \
	&&  docker-php-ext-enable redis

WORKDIR /var/www

EXPOSE 9000