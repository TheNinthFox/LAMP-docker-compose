FROM php:7.1.9-apache 

WORKDIR /var/www/app

COPY ./000-default.conf /etc/apache2/sites-available/000-default.conf

RUN apt-get update && apt-get install -y libzip-dev zip libpng-dev libmcrypt-dev git
RUN usermod -u 1000 www-data

RUN docker-php-ext-configure zip --with-libzip
RUN docker-php-ext-install mysqli mbstring gd mcrypt zip pdo pdo_mysql opcache

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '93b54496392c062774670ac18b134c3b3a95e5a5e5c8f1a9f115f203b75bf9a129d5daa8ba6a13e2cc8a1da0806388a8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN mv composer.phar /usr/bin/composer
RUN php -r "unlink('composer-setup.php');"

RUN apt-get install apache2-utils
RUN a2enmod rewrite
