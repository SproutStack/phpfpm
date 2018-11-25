FROM php:5.6-fpm-alpine

MAINTAINER Rhys Botfield <rhys@sproutdesk.co.uk>

ENV _BUILD_DEPS \
		libpng-dev \
		jpeg-dev \
		freetype-dev \
		icu-dev \
		libmcrypt-dev \
		libxml2-dev \
		libxslt-dev

RUN apk add --no-cache libpng \
		libjpeg-turbo \
		freetype \
		icu \
		libmcrypt \
		libxslt \
		${_BUILD_DEPS} \
	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr --with-freetype-dir=/usr \
	&& docker-php-ext-install gd pdo_mysql soap xsl mysqli intl bcmath zip \
	&& apk del ${_BUILD_DEPS}

# PECL extensions
RUN apk add --no-cache ${PHPIZE_DEPS} \
	&& pecl install -o -f redis xdebug-2.5.5 \
	&& docker-php-ext-enable redis xdebug \
	&& apk del ${PHPIZE_DEPS}

RUN echo "always_populate_raw_post_data = -1" >> /usr/local/etc/php/conf.d/deprecated.ini

RUN mkdir /var/log/php-fpm/
RUN rm /usr/local/etc/php-fpm.d/zz-docker.conf
ADD www.conf /usr/local/etc/php-fpm.d/www.conf

ADD xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

RUN apk add --no-cache ssmtp
ADD ssmtp.conf /etc/ssmtp/ssmtp.conf
