FROM    php-cli


RUN     yum update -y \
        && yum install -y \
            php-fpm \
        && yum clean all \
        && rm -rf /var/chache/yum/*

RUN     useradd php-fpm

COPY    ./etc/php-fpm.conf /etc/php-fpm.conf

COPY    ./etc/php-fpm.d/www.conf /etc/php-fpm.d/www.conf

EXPOSE  9000

ENTRYPOINT ["/usr/sbin/php-fpm", "-F"]
