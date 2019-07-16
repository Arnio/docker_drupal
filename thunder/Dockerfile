# FROM arnio/ubuntu-fpm7.3:1.0
# FROM arnio/centos7-fpm7.3:1.0
FROM arnio/alpine-fpm7.3:1.0

# RUN cd /var/www/html && \
#    composer create-project burdamagazinorg/thunder-project thunder --no-interaction && \
#    cd /var/www/html/thunder/ && \
#    composer install --no-progress --profile --prefer-dist --verbose --no-interaction && \
#    chown -R www-data:www-data /var/www/html/thunder/ && \
#    chmod -R 755 /var/www/html/thunder/
ADD /thunder-8.x-2.44-core.tar.gz /var/www/html/

RUN ls -la /var/www/html/ 

RUN cd /var/www/html/thunder-8.x-2.44 && \
    composer install --no-progress --profile --prefer-dist && \
    chown -R nginx:nginx /var/www/html




# COPY ./default /etc/nginx/sites-available/default
COPY ./default /etc/nginx/conf.d/default.conf
EXPOSE 80