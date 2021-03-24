FROM php:7.4-apache

LABEL maintainer="Víctor R. Rodríguez Domínguez <vrodriguez@dinahosting.com"

# Install modules and composer
RUN export DEBIAN_FRONTEND=noninteractive \
    && apt-get update && apt-get dist-upgrade -y \
    && apt-get install -y git zlib1g-dev libzip-dev wget \
    && docker-php-ext-install zip mysqli pdo pdo_mysql \
    && wget https://getcomposer.org/composer-stable.phar -O /usr/bin/composer \
    && chmod a+x /usr/bin/composer \
    && composer create-project laminas-api-tools/api-tools-skeleton /var/www/html/ \
    && chown -R www-data: /var/www/html \
    && a2enmod rewrite \
    && sed -ri -e 's!/var/www/html!/var/www/html/public!g' /etc/apache2/sites-available/*.conf \
    && apt-get autoremove -y && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


