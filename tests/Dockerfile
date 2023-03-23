FROM php:8.2-alpine

RUN apk add --no-cache curl-dev chromium chromium-chromedriver sqlite-dev linux-headers libxml2-dev libpng-dev libzip-dev zlib-dev icu-dev
RUN apk add --update nodejs npm
RUN docker-php-ext-configure curl \
    && docker-php-ext-configure gd \
    && docker-php-ext-configure xml \
    && docker-php-ext-configure zip \
    && docker-php-ext-configure pdo_sqlite \
    && docker-php-ext-install curl \
    && docker-php-ext-install gd \
    && docker-php-ext-install intl \
    && docker-php-ext-install xml \
    && docker-php-ext-install zip \
    && docker-php-ext-install pdo_sqlite

RUN apk add --no-cache $PHPIZE_DEPS \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug

RUN npm install --global yarn
RUN curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer
