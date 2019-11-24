# Dockerize a PHP application

This repository is extending https://github.com/TrafeX/docker-php-nginx with changes to use it as a base docker image when dockerizing a PHP application.

[![Docker Pulls](https://img.shields.io/docker/pulls/trafex/alpine-nginx-php7.svg)](https://hub.docker.com/r/trafex/alpine-nginx-php7/)
[![Docker image layers](https://images.microbadger.com/badges/image/trafex/alpine-nginx-php7.svg)](https://microbadger.com/images/trafex/alpine-nginx-php7)

For full description of the original repository please visit https://github.com/TrafeX/docker-php-nginx directly. To provide a brief summary here:
* based on Alpine Linux distribution
* running Nginx and PHP-FPM in from supervisord

## Expected usage

```
FROM docker-php-nginx  # build an image from this repository as base
WORKDIR /var/www
COPY /<your_directory> /var/www
```

## Adding composer

If you need composer in your project, here's an easy way to add it;

```dockerfile
FROM trafex/alpine-nginx-php7:latest

# Install composer from the official image
COPY --from=composer /usr/bin/composer /usr/bin/composer

# Run composer install to install the dependencies
RUN composer install --optimize-autoloader --no-interaction --no-progress
```