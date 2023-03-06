FROM php:8.1.0-fpm-buster

# Install selected extensions and other stuff
RUN apt-get update && apt-get upgrade -y && apt-get install -y libzip-dev && apt-get install -y libpq-dev

RUN docker-php-ext-install pdo pdo_pgsql

RUN docker-php-ext-install zip exif pcntl

COPY --from=composer /usr/bin/composer /usr/bin/composer
RUN composer self-update

WORKDIR "/application"
COPY . .

RUN composer install

EXPOSE 8000
CMD ["php", "artisan", "serve"] 