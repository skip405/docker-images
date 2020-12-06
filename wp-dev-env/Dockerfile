FROM wordpress

ENV X_DEBUG_VERSION 2.9.8
ENV PHPUNIT_VERSION 7

# installing xdebug and enabling remote connections (e.g. PHPStorm)
RUN pecl install xdebug-$X_DEBUG_VERSION; \
    docker-php-ext-enable xdebug; \
    echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

# installing svn and mysql client
RUN apt-get update && apt-get install -y subversion mariadb-client

# installing WP-CLI
RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar; \
    chmod +x wp-cli.phar; \
    mv wp-cli.phar /usr/local/bin/wp; \
    wp --allow-root --version

# installing PHPUnit, -L flag is for a redirect to the latest version
RUN curl -O -L https://phar.phpunit.de/phpunit-$PHPUNIT_VERSION.phar; \
    chmod +x phpunit-$PHPUNIT_VERSION.phar; \
    mv phpunit-$PHPUNIT_VERSION.phar /usr/local/bin/phpunit; \
    phpunit --version