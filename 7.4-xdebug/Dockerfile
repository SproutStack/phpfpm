FROM sproutstack/phpfpm:7.4

MAINTAINER Rhys Botfield <rhys@sproutdesk.co.uk>

RUN apk add --no-cache ${PHPIZE_DEPS} \
	&& pecl install -o -f xdebug-beta \
	&& docker-php-ext-enable xdebug \
	&& apk del ${PHPIZE_DEPS}

ADD xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

#ADD ssmtp.conf /etc/ssmtp/ssmtp.conf
#ADD www.conf /usr/local/etc/php-fpm.d/www.conf
