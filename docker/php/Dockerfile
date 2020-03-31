# ./docker/php/Dockerfile
FROM php:7.4-fpm

RUN docker-php-ext-install pdo_mysql

RUN pecl install apcu

RUN apt-get update && \
apt-get install -y \
libzip-dev

RUN docker-php-ext-install zip
RUN docker-php-ext-enable apcu

RUN echo "$(curl -sS https://composer.github.io/installer.sig) -" > composer-setup.php.sig \
        && curl -sS https://getcomposer.org/installer | tee composer-setup.php | sha384sum -c composer-setup.php.sig \
        && php composer-setup.php && rm composer-setup.php* \
        && chmod +x composer.phar && mv composer.phar /usr/local/bin/composer

WORKDIR /usr/src/app

# /répertoire par défaut /nous copions notre application actuelle dans notre ordinateur,
COPY apps/my-symfony-app /usr/src/app

RUN PATH=$PATH:/usr/src/apps/vendor/bin:bin