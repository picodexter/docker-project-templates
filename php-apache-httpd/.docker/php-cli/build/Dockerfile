FROM php:7.4-fpm

ENV PHP_IDE_CONFIG="serverName=Project Server"

RUN echo '[X] START OF CUSTOMIZATION BUILD' \
    && echo '[-] Updating Aptitude package cache ...' \
    && apt-get update \
    && echo '[-] Installing system packages gpg, unzip ...' \
    && apt-get install -y gpg unzip \
    && echo '[-] Installing PHP PECL extension xdebug ...' \
    && pecl install xdebug \
    && echo '[-] Installing PHP extension pdo_mysql ...' \
    && docker-php-ext-install pdo_mysql \
    && echo '[-] Enabling PHP extension xdebug ...' \
    && docker-php-ext-enable xdebug \
    && echo '[-] Installing Composer ...' \
    && (php -r "readfile('https://getcomposer.org/installer');" | php -- --install-dir=/usr/local/bin --filename=composer) \
    && echo '[o] Installing PHIVE ...' \
        && echo '   [-] Downloading PHIVE PHAR file ...' \
        && curl -Lo /tmp/phive.phar https://phar.io/releases/phive.phar \
        && echo '   [-] Downloading PHIVE PHAR file signature ...' \
        && curl -Lo /tmp/phive.phar.asc https://phar.io/releases/phive.phar.asc \
        && echo '   [-] Fetching PHIVE GPG public key ...' \
        && gpg --keyserver pool.sks-keyservers.net --recv-keys 0x9D8A98B29B2D5D79 \
        && echo '   [-] Verifying PHIVE PHAR file signature ...' \
        && gpg --verify /tmp/phive.phar.asc /tmp/phive.phar \
        && echo '   [-] Setting PHIVE PHAR file as executable for everyone ...' \
        && chmod +x /tmp/phive.phar \
        && echo '   [-] Move PHIVE PHAR file to /usr/local/bin/ ...' \
        && mv /tmp/phive.phar /usr/local/bin/phive \
        && echo '   [-] Deleting PHIVE PHAR file signature ...' \
        && rm /tmp/phive.phar.asc \
    && echo '[o] Finished installing PHIVE.' \
    && echo '[-] Installing unsigned PHIVE package phpmd/phpmd ...' \
    && phive install -g --force-accept-unsigned phpmd/phpmd \
    && echo '[-] Installing PHIVE packages friendsofphp/php-cs-fixer, phploc, phpstan/phpstan ...' \
    && phive install -g --trust-gpg-keys 0xE82B2FB314E9906E,0x4AA394086372C20A,0xCF1A108D0E7AE720 friendsofphp/php-cs-fixer phploc phpstan/phpstan \
    && echo '[-] Clearing Aptitude package cache ...' \
    && rm -rf /var/lib/apt/lists/* \
    && echo '[X] END OF CUSTOMIZATION BUILD'

WORKDIR /var/www/html
