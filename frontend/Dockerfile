FROM debian:stable

ENV APACHE_LOG_DIR /var/log/apache2

COPY ./dist/mystuff/ /var/www/html
COPY ./.htaccess /var/www/html

RUN set -eux; \
    apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y apache2 && \
    ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log"; \
	  ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log"; \
	  ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"; \
    a2enmod rewrite headers proxy proxy_http

COPY ./apache2.conf /etc/apache2/apache2.conf
COPY ./default-ssl.conf /etc/apache2/sites-available/default-ssl.conf

EXPOSE 80

CMD ["/usr/sbin/apache2ctl", "-D" ,"FOREGROUND"]
