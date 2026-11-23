FROM debian:stable

RUN apt-get update \
    && apt-get install -y --no-install-recommends apache2 \
    && rm -rf /var/lib/apt/lists/* \
    && a2enmod proxy proxy_http \
    && rm -f /var/www/html/index.html

COPY cafefe-proxy.conf /etc/apache2/conf-available/cafefe-proxy.conf

RUN a2enconf cafefe-proxy \
    && apache2ctl configtest

EXPOSE 80
CMD ["apache2ctl", "-D", "FOREGROUND"]