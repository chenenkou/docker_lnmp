FROM php:7.1.18-fpm

# 复制php配置文件
COPY php.ini /usr/local/etc/php/php.ini

# 添加更新源
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak
ADD sources.list /etc/apt/sources.list
RUN apt-get update && \
        pecl channel-update https://pecl.php.net/channel.xml

# 安装apt-utils
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install --assume-yes apt-utils

# 安装GD和mcrypt扩展
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

# 安装mysqli和pdo扩展
RUN docker-php-ext-install mysqli pdo_mysql

# 安装mongodb扩展
#RUN pecl install mongodb \
#    && docker-php-ext-enable mongodb
COPY mongodb-1.6.1.tgz /tmp
RUN pecl install /tmp/mongodb-1.6.1.tgz && \
    docker-php-ext-enable mongodb

# 安装redis扩展
#RUN pecl install redis \
#	&&  docker-php-ext-enable redis
COPY redis-5.1.1.tgz /tmp
RUN pecl install /tmp/redis-5.1.1.tgz && \
    docker-php-ext-enable redis

# 清理
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    rm /var/log/lastlog /var/log/faillog

#WORKDIR /var/www/html

EXPOSE 9000