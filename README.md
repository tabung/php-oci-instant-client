# php-oci-instant-client
This repository contains Oracle Instant Client 11 installation for three different PHP versions, which are PHP 5.6, 7.4, and 8.1. This repository is used for developing or running applications that connect to Oracle 9i databases

# Operating Systems
- Alpine Linux 3.8 for PHP 5.6
- Alpine Linux 3.15 for PHP 7.4
- Alpine Linux 3.17 for PHP 8.1

# Web Server
- Nginx

# PHP Versions
- php5.6
- php7.4
- php8.1

# Usage
Build the Docker image with the following command:
```
docker build -t my-php-app .
```
Run a Docker container with the following command:
```
docker run -p 8080:80 -v /path/to/my/php/app:/var/www/html my-php-app
```
