FROM php:8.2-fpm

# Set ARG UID dan GID dengan default value
ARG UID=1000
ARG GID=1000

# Tambahkan grup dan user hanya jika belum ada
RUN getent group www-data || addgroup --gid $GID www-data \
    && id -u www-data &>/dev/null || adduser --uid $UID --gid $GID --shell /bin/bash --disabled-password --gecos "" www-data


# Instalasi package yang diperlukan
RUN apt-get update \
  && apt-get install -y build-essential zlib1g-dev default-mysql-client curl gnupg procps vim git unzip libzip-dev libpq-dev \
  && docker-php-ext-install zip pdo_mysql pdo_pgsql pgsql

RUN apt-get install -y libicu-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl

RUN apt-get update \
    && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli

# Instalasi pcov
RUN pecl install pcov && docker-php-ext-enable pcov

# Node.js, NPM, Yarn
RUN curl -sL https://deb.nodesource.com/setup_20.x | bash -
RUN apt-get install -y nodejs
RUN npm install npm@latest -g
RUN npm install yarn -g

# Instalasi Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

# Set environment variables untuk Composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin
RUN composer config --global process-timeout 3600
RUN composer global require "laravel/installer"

WORKDIR /root
RUN git clone https://github.com/seebi/dircolors-solarized

# Set ownership agar sesuai dengan user www-data
EXPOSE 5173   
WORKDIR /var/www
RUN chown -R www-data:www-data /var/www
