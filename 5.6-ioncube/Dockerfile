FROM sproutstack/phpfpm:5.6

MAINTAINER Rhys Botfield <rhys@sproutdesk.co.uk>

RUN curl -o ioncube_loaders_lin_x86-64.tar.gz http://downloads3.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz \
	&& tar xfz ioncube_loaders_lin_x86-64.tar.gz \
	&& cp ioncube/ioncube_loader_lin_5.6.so /usr/local/lib/php/extensions/no-debug-non-zts-20131226/ \
	&& echo "zend_extension=ioncube_loader_lin_5.6.so" > /usr/local/etc/php/conf.d/00_docker-php-ext-ioncube_loader_lin_5.6.ini \
	&& rm -Rf ioncube_loaders_lin_x86-64.tar.gz ioncube
