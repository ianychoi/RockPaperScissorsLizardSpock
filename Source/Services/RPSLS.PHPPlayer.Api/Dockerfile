FROM php:7.3.2-apache-stretch
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer
COPY ./src .
COPY --chown=www-data:www-data ./src /srv/app
COPY ./src/.apache/vhost.conf /etc/apache2/sites-available/000-default.conf
WORKDIR /srv/app
ENV LOG_CHANNEL errorlog
RUN docker-php-ext-install mbstring \
 && a2enmod rewrite negotiation \
 && docker-php-ext-install opcache