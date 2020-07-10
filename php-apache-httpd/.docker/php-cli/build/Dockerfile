FROM php:7.4-fpm

ENV PHP_IDE_CONFIG="serverName=Project Server"

RUN echo '[X] START OF CUSTOMIZATION BUILD' \
    && echo '[-] Updating Aptitude package cache ...' \
    && apt-get update \
    && echo '[-] Installing system package unzip ...' \
    && apt-get install -y unzip \
    && echo '[-] Installing PHP PECL extension xdebug ...' \
    && pecl install xdebug \
    && echo '[-] Installing PHP extension pdo_mysql ...' \
    && docker-php-ext-install pdo_mysql \
    && echo '[-] Enabling PHP extension xdebug ...' \
    && docker-php-ext-enable xdebug \
    && echo '[-] Installing Composer ...' \
    && (php -r "readfile('https://getcomposer.org/installer');" | php -- --install-dir=/usr/local/bin --filename=composer) \
    && echo '[-] Clearing Aptitude package cache ...' \
    && rm -rf /var/lib/apt/lists/* \
    && echo '[X] END OF CUSTOMIZATION BUILD'

WORKDIR /var/www/html
