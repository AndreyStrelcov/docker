FROM php:7.4-fpm

RUN docker-php-ext-install mysqli 
RUN docker-php-ext-install pdo pdo_mysql

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN pecl install xdebug-3.1.6 \
    && docker-php-ext-enable xdebug

COPY conf.d/* $PHP_INI_DIR/conf.d/    