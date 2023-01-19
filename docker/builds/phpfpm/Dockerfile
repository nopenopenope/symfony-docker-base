FROM php:8.1-fpm

ENV PHP_IDE_CONFIG="serverName=symfony-base"
ENV BASE_DIR /var/www
ENV SYMFONY_DIR ${BASE_DIR}/html

RUN docker-php-ext-install pdo_mysql
RUN pecl install apcu
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

RUN apt-get update && apt-get install -y --no-install-recommends \
        git \
        vim \
        gpg \
        gpg-agent \
        zlib1g-dev \
        libjpeg-dev \
        libicu-dev \
		libpng-dev \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
        zip \
		libzip-dev

RUN docker-php-ext-enable opcache
RUN docker-php-ext-configure zip
RUN docker-php-ext-install \
        intl \
        zip \
		exif \
		pdo \
		pdo_mysql

RUN docker-php-ext-configure gd \
    --with-jpeg=/usr/include/ \
    --with-freetype=/usr/include/

RUN docker-php-ext-install gd

RUN apt-get purge -y \
		zlib1g-dev \
		libicu-dev \
		libpng-dev \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
		libmcrypt-dev

ADD ./etc/php.ini /usr/local/etc/php/php.ini
ADD ./etc/php-cli.ini /usr/local/etc/php/php-cli.ini

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

RUN apt-get install -y unzip

RUN usermod -u 1000 www-data
RUN mkdir /.composer && chown -R 1000:1000 /.composer && chmod 775 /.composer
RUN export PATH="$PATH:${SYMFONY_DIR}/vendor/bin:bin"
RUN export PATH="$PATH:${SYMFONY_DIR}/bin:bin"
RUN export PATH="$PATH:/.composer/vendor/bin"

WORKDIR ${SYMFONY_DIR}
RUN chown -R www-data:1000 ${BASE_DIR}
