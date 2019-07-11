FROM arnio/ubuntu-fpm7.3:1.0

#RUN git clone --branch 8.7.x https://git.drupalcode.org/project/drupal.git
ADD /drupal-8.7.4.tar.gz /var/www/html/

# RUN cp -R drupal/ html && \
#     rm -rf drupal html/.git /var/www/html && \
#     mv -f html /var/www/ && \
RUN cd /var/www/html/drupal-8.7.4 && \
    composer install --no-progress --profile --prefer-dist && \
    chown -R www-data:www-data /var/www/html 

COPY ./default /etc/nginx/sites-available/default
# COPY ./start.sh /usr/local/bin/

# RUN chmod u+x /usr/local/bin/start.sh
EXPOSE 80 
ENTRYPOINT [ "start.sh" ]
