FROM php:7.4-fpm

RUN echo '[X] START OF CUSTOMIZATION BUILD' \
    && echo '[-] Installing PHP extension pdo_mysql ...' \
    && docker-php-ext-install pdo_mysql \
    && echo '[X] END OF CUSTOMIZATION BUILD'
