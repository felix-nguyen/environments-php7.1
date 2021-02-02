FROM    amazonlinux:2

RUN     yum update -y \
        && amazon-linux-extras install -y php7.1 \
        && yum install -y \
            git \
            gcc \
            gcc-c++ \
            make \
            libpng-devel \
            libtool \
            nasm \
            php-bcmath \
            php-cli \
            php-common \
            php-dba \
            php-dbg \
            php-devel \
            php-gd \
            php-intl \
            php-json \
            php-mbstring \
            php-mysqlnd \
            php-pdo \
            php-pear \
            php-pecl-redis \
            php-process \
            php-xml \
            php-xmlrpc \
            php-opcache \
            php-pecl-mcrypt \
            php-pecl-zip \
            ipa-gothic-fonts \
        && yum install -y \
            https://dl.google.com/linux/direct/google-chrome-stable_current_x86_64.rpm \
        && yum erase -y \
            php-fpm \
        && yum clean all \
        && rm -rf /var/chache/yum/*

# Install Composer, PHPCS,
# PHPMetrics, PHPDepend, PHPMessDetector, PHPCopyPasteDetector
RUN curl -s http://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && composer global require 'squizlabs/php_codesniffer' \
        'phpmetrics/phpmetrics' \
        'pdepend/pdepend' \
        'phpmd/phpmd' \
        'sebastian/phpcpd'

COPY    ./etc/php.ini /etc/php.ini

COPY    ./usr/bin/php-cli-entrypoint /usr/bin/

CMD     ["/usr/bin/php", "-i"]
