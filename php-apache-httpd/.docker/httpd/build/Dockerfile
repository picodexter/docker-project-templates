FROM httpd:2.4-alpine

RUN echo '[X] START OF CUSTOMIZATION BUILD' \
    && echo '[-] Enabling Apache HTTPd modules proxy, proxy_fcgi, rewrite ...' \
    && sed -i \
        -e 's/^#\(LoadModule proxy_module .*mod_proxy\.so\)$/\1/' \
        -e 's/^#\(LoadModule proxy_fcgi_module .*mod_proxy_fcgi\.so\)$/\1/' \
        -e 's/^#\(LoadModule rewrite_module .*mod_rewrite\.so\)$/\1/' \
        /usr/local/apache2/conf/httpd.conf \
    && echo '[-] Including Apache HTTPd vHosts configuration file ...' \
    && sed -i -e 's/^#\(Include .*httpd-vhosts\.conf\)$/\1/' /usr/local/apache2/conf/httpd.conf \
    && echo '[X] END OF CUSTOMIZATION BUILD'
