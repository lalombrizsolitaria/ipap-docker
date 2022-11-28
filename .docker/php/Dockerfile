FROM php:8.1-fpm-buster
ARG TIMEZONE

# IMAGEN OFICIAL DE PHP 8.1

# COPIO php.ini del anfitrion para reemplazar el del contenedor, con configuraciones basicas.
COPY php.ini /usr/local/etc/php/conf.d/docker-php-config.ini

# SE INSTALAN LIBRERIAS BASICAS NECESARIAS PARA EJECUTAR UN PROYECTO SYMFONY
RUN apt-get update && apt-get install -y \
    gnupg \
    g++ \
    procps \
    openssl \
    git \
    unzip \
    zlib1g-dev \
    libzip-dev \
    libfreetype6-dev \
    libpng-dev \
    libjpeg-dev \
    libicu-dev  \
    libonig-dev \
    libxslt1-dev \
    acl \
    && echo 'alias sf="php bin/console"' >> ~/.bashrc

RUN docker-php-ext-configure gd --with-jpeg --with-freetype 

RUN docker-php-ext-install \
    pdo pdo_mysql zip xsl gd intl opcache exif mbstring

# DEFINO TIMEZONE
RUN ln -snf /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && echo ${TIMEZONE} > /etc/timezone \
    && printf '[PHP]\ndate.timezone = "%s"\n', ${TIMEZONE} > /usr/local/etc/php/conf.d/tzone.ini \
    && "date"

# INSTALO COMPOSER COMO GESTOR DE PAQUETES
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# SE ESTABLECE COMO DIRECTORIO PRINCIPAL
WORKDIR /var/www/symfony