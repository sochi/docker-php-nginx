# Dockerize a PHP application

This repository is extending https://github.com/TrafeX/docker-php-nginx with changes to use it as a base docker image when dockerizing a PHP application.

For full description of the original repository please visit https://github.com/TrafeX/docker-php-nginx directly. To provide a brief summary here:
* based on Alpine Linux distribution
* running Nginx and PHP-FPM in from supervisord

## Building the image locally

```
docker build -t docker-php-nginx .
```

## Expected usage

```
FROM docker-php-nginx  # build an image from this repository as base
WORKDIR /var/www
COPY /<your_directory> /var/www
```
