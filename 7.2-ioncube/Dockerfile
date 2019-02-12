FROM sproutstack/phpfpm:7.2

MAINTAINER Rhys Botfield <rhys@sproutdesk.co.uk>

RUN curl -o ioncube_loaders_lin_x86-64.tar.gz http://downloads3.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz \
	&& tar xfz ioncube_loaders_lin_x86-64.tar.gz \
	&& cp ioncube/ioncube_loader_lin_7.2.so /usr/local/lib/php/extensions/no-debug-non-zts-20170718/ \
	&& echo "zend_extension=ioncube_loader_lin_7.2.so" > /usr/local/etc/php/conf.d/00_docker-php-ext-ioncube_loader_lin_7.2.ini \
	&& rm -Rf ioncube_loaders_lin_x86-64.tar.gz ioncube
