# FROM arnio/ubuntu-fpm7.3:1.0
# FROM arnio/centos7-fpm7.3:1.0
FROM arnio/alpine-fpm7.3:1.0

ADD /drupal-8.8.2.tar.gz /var/www/html/

RUN cd /var/www/html/drupal-8.8.2 && \
    composer install --no-progress --profile --prefer-dist && \
    chown -R nginx:nginx /var/www/html 

COPY ./default /etc/nginx/conf.d/default.conf
EXPOSE 80 
ENTRYPOINT [ "start.sh" ]
