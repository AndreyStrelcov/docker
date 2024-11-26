FROM php:7.4-fpm

RUN docker-php-ext-install mysqli 
RUN docker-php-ext-install pdo pdo_mysql

RUN apt-get update \
     && apt-get install -y libzip-dev \
     && docker-php-ext-install zip

RUN apt-get update -y && apt-get install -y libpng-dev

RUN apt-get update && \
    apt-get install -y \
        zlib1g-dev
     
RUN docker-php-ext-install gd   

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN pecl install xdebug-3.1.6 \
    && docker-php-ext-enable xdebug
 
COPY conf.d/* $PHP_INI_DIR/conf.d/    

RUN groupadd -g 1000 myuser && \
    useradd -u 1000 -g 1000 -s /bin/bash -m myuser && \
    usermod -aG sudo myuser && \
    echo 'myuser:mypass' | chpasswd

USER myuser

