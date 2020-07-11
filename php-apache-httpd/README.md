# Project Template - PHP & Apache HTTPd

## Overview

Basic assumptions:

-   Apache HTTPd 2.4
-   PHP 7.4
-   Symfony 5
-   IDE supports Xdebug incoming connections and project server name is set to "Project Server" 

## Application Stacks

### Web Stack

-   httpd - Apache HTTPd web server
    -   Loaded modules:
        -   proxy
        -   proxy_fcgi
-   php-fpm - PHP FPM application server
    -   Loaded extensions:
        -   pdo_mysql
        -   xdebug

### CLI Stack

-   php-cli - PHP CLI
    -   Loaded extensions:
        -   pdo_mysql
        -   xdebug
    -   Tools:
        -   Composer
        -   PHIVE
        -   PHP CS Fixer
        -   phploc
        -   PHPMD
        -   PHPStan
