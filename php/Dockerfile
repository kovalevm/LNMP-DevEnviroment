FROM php:7.1-fpm

RUN docker-php-ext-install pdo_mysql

RUN yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini

# Install Node.js and other dependencies
RUN apt-get update && \
    apt-get -y install curl && \
    curl -sL https://deb.nodesource.com/setup | bash - && \
    apt-get -y install python build-essential nodejs

# Packaged dependencies
RUN apt-get update && apt-get install -y \
	bash-completion \
	git \
	vim \
	vim-common \
	zip

# Install nodemon
RUN npm install -g nodemon

RUN npm install -g bower
RUN npm install -g grunt
RUN npm install -g gulp


RUN curl -sS https://getcomposer.org/installer | \
    php -- --install-dir=/usr/bin/ --filename=composer


