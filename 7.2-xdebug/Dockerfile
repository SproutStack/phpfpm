FROM php:7.2-fpm-alpine

MAINTAINER Rhys Botfield <rhys@sproutdesk.co.uk>

ENV _BUILD_DEPS \
		libpng-dev \
		jpeg-dev \
		freetype-dev \
		icu-dev \
		libxml2-dev \
		libxslt-dev

RUN apk add --no-cache libpng \
		libjpeg-turbo \
		freetype \
		icu \
		libxslt \
		${_BUILD_DEPS} \
	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr --with-freetype-dir=/usr \
	&& docker-php-ext-install gd pdo_mysql soap xsl mysqli intl bcmath zip \
	&& apk del ${_BUILD_DEPS}

# PECL extensions
RUN apk add --no-cache ${PHPIZE_DEPS} \
	&& pecl install -o -f redis xdebug-2.6.0 \
	&& docker-php-ext-enable redis xdebug \
	&& apk del ${PHPIZE_DEPS}

RUN mkdir /var/log/php-fpm/
RUN rm /usr/local/etc/php-fpm.d/zz-docker.conf
ADD www.conf /usr/local/etc/php-fpm.d/www.conf

ADD xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
