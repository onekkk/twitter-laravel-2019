FROM php:7.2-fpm

WORKDIR /var/www/html


# install composer
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer
RUN apt-get update \
&& apt-get install -y \
git \
zip \
unzip \
vim

RUN apt-get update \
    && apt-get install -y libpq-dev \
    && docker-php-ext-install pdo_mysql pdo_pgsql

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev
RUN apt-get install -y libjpeg-dev \
	gcc \
	make \
    	libpng-dev \
    	git \
    	unzip \
    	vim \
	libmcrypt-dev \
	curl \
        gnupg \
	libfreetype6-dev \
	&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install gd

COPY ./app.php /root/app.php 
COPY ./php.ini $PHP_INI_DIR/php.ini
