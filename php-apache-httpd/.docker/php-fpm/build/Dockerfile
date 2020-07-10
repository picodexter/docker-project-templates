FROM php:7.4-fpm

RUN echo '[X] START OF CUSTOMIZATION BUILD' \
    && echo '[-] Installing PHP PECL extension xdebug ...' \
    && pecl install xdebug \
    && echo '[-] Installing PHP extension pdo_mysql ...' \
    && docker-php-ext-install pdo_mysql \
    && echo '[-] Enabling PHP extension xdebug ...' \
    && docker-php-ext-enable xdebug \
    && echo '[X] END OF CUSTOMIZATION BUILD'
