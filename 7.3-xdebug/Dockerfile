FROM sproutstack/phpfpm:7.3

MAINTAINER Rhys Botfield <rhys@sproutdesk.co.uk>

RUN apk add --no-cache ${PHPIZE_DEPS} \
	&& pecl install -o -f xdebug-beta \
	&& docker-php-ext-enable xdebug \
	&& apk del ${PHPIZE_DEPS}

ADD xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
