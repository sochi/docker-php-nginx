# Dockerize a PHP application

This repository is extending https://github.com/TrafeX/docker-php-nginx with changes to use it as a base docker image when dockerizing a PHP application.

For full description of the original repository please visit https://github.com/TrafeX/docker-php-nginx directly. To provide a brief summary here:
* based on Alpine Linux distribution
* running Nginx and PHP-FPM in from supervisord

## Building the image locally

```shell
docker build -t docker-php-nginx .
```

## Expected usage

```Dockerfile
# build an image from this repository as base image
FROM docker-php-nginx
WORKDIR /var/www
COPY --chown=nginx <your_directory>/ /var/www

# append other configuration to the server if necessary
# for instance we can set expiration headers for cache, or to disable access
# logging on favicon.ico and robots.txt
COPY <your_configuration_file>.conf /etc/nginx/conf.d/default.conf.add
```
