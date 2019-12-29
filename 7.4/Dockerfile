FROM php:7.4-fpm-alpine

MAINTAINER Rhys Botfield <rhys@sproutdesk.co.uk>

ENV _BUILD_DEPS \
		libpng-dev \
		jpeg-dev \
		freetype-dev \
		icu-dev \
		libxml2-dev \
		libxslt-dev \
		libzip-dev

RUN apk add --no-cache libpng \
		libjpeg-turbo \
		freetype \
		icu \
		libxslt \
		libzip \
		${_BUILD_DEPS} \
	&& docker-php-ext-configure gd --with-jpeg --with-freetype \
	&& docker-php-ext-install gd pdo_mysql soap xsl mysqli intl bcmath zip \
	&& apk del ${_BUILD_DEPS}

# PECL extensions
RUN apk add --no-cache ${PHPIZE_DEPS} \
	&& pecl install -o -f redis \
	&& docker-php-ext-enable redis \
	&& apk del ${PHPIZE_DEPS}

RUN mkdir /var/log/php-fpm/
RUN rm /usr/local/etc/php-fpm.d/zz-docker.conf
ADD www.conf /usr/local/etc/php-fpm.d/www.conf

RUN apk add --no-cache ssmtp
ADD ssmtp.conf /etc/ssmtp/ssmtp.conf
