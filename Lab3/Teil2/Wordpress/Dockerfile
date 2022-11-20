# syntax=docker/dockerfile:1
FROM debian:jessie

ENV DEBIAN_FRONTEND noninteractive
ENV container docker

RUN apt-get update

RUN apt-get install -y --force-yes --no-install-recommends wget apache2 php5 libapache2-mod-php5 php5-mcrypt php5-mysql unzip ca-certificates

RUN echo "<Directory /var/www/html/>AllowOverride All</Directory>" >> /etc/apache2/apache2.conf
RUN a2enmod rewrite

RUN cd /var/www/html && \
    wget https://wordpress.org/latest.zip && \
    unzip -q latest.zip && \
    chown -R www-data:www-data /var/www/html/wordpress && \
    chmod -R 755 /var/www/html/wordpress && \
    mkdir -p /var/www/html/wordpress/wp-content/uploads && \
    chown -R www-data:www-data /var/www/html/wordpress/wp-content/uploads

expose 80
expose 443

VOLUME ["/var/www/html"]

CMD apachectl -D FOREGROUND
