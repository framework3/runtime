FROM php:8.3-apache

WORKDIR /var/www/html

COPY security.conf /etc/apache2/conf-available/security.conf
COPY php.ini /usr/local/etc/php/php.ini
COPY 000-default.conf /etc/apache2/sites-available/000-default.conf
COPY supervisord.conf /etc/supervisor/supervisord.conf
RUN a2enmod rewrite

# Create a non-root runtime user with group 33 (apache's www-data group)
RUN groupadd --force -g 33 runtime
RUN useradd -ms /bin/bash --no-user-group -g 33 -u 1337 runtime

# Run supervisor on start
CMD ["/usr/bin/supervisord"]