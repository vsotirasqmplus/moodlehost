FROM moodlehq/moodle-php-apache:7.3
MAINTAINER Matthias Opitz <m.opitz@qmul.ac.uk>
# v.1.0.2 - 2019-12-16

RUN apt-get update
RUN cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini
RUN pecl install xdebug-2.8.1
RUN echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20180731/xdebug.so" >> /usr/local/etc/php/php.ini
RUN echo "[xdebug]" >> /usr/local/etc/php/php.ini

RUN echo "xdebug.remote_enable=1" >> /usr/local/etc/php/php.ini && \
	echo "xdebug.remote_autostart=0" >> /usr/local/etc/php/php.ini && \
	echo "xdebug.remote_handler=dbgp" >> /usr/local/etc/php/php.ini && \
	echo "xdebug.idekey=PHPSTORM" >> /usr/local/etc/php/php.ini && \
	echo "xdebug.remote_connect_back=1" >> /usr/local/etc/php/php.ini && \
	echo "xdebug.remote_port=9000" >> /usr/local/etc/php/php.ini && \
	echo "xdebug.remote_host=172.17.0.1" >> /usr/local/etc/php/php.ini

RUN 	yes "" | apt install mcrypt
RUN	pecl update-channels && yes "" | pecl install -f channel://pecl.php.net/mcrypt-1.0.1
RUN	echo "extension=mcrypt.so" >> /usr/local/etc/php/php.ini
RUN 	sed -i 's/128M/1G/g' /usr/local/etc/php/php.ini
RUN service apache2 start &


