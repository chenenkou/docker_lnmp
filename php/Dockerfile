FROM php:7.1.18-fpm

COPY php.ini /usr/local/etc/php/php.ini

# 添加更新源
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak
ADD sources.list /etc/apt/sources.list
RUN apt-get update && \
        pecl channel-update https://pecl.php.net/channel.xml

RUN docker-php-ext-install pdo_mysql

# install mongodb ext
RUN pecl install mongodb \
    && docker-php-ext-enable mongodb

# install redis ext
RUN pecl install -o -f redis \
	&&  rm -rf /tmp/pear \
	&&  docker-php-ext-enable redis

#WORKDIR /var/www

EXPOSE 9000