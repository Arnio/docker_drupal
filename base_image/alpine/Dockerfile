FROM alpine:3.10
# RUN apk add --no-cache mysql-client
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone 
#     apt-get -y update && apt-get -y remove --purge apache2 && apt-get -y install software-properties-common && \
#     add-apt-repository -y ppa:ondrej/php 
RUN apk update && apk upgrade
RUN apk add nginx composer
RUN apk add curl \
            git \
            unzip \
            php7 \
            php7-fpm \
            php7-common \
            php7-mbstring \
            php7-xmlrpc \
            php7-soap \
            php7-gd \
            php7-xml \
            php7-intl \
            php7-mysqli \
            php7-cli \
            php7-tidy \
            php7-recode \
            php7-zip \
            php7-curl 
            
RUN sed -i -e 's/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/g' /etc/php7/php.ini 
# RUN curl -sS https://getcomposer.org/installer -o composer-setup.php 
# RUN php composer-setup.php --install-dir=/usr/local/bin --filename=composer 


COPY ./default /etc/nginx/sites-available/default
COPY ./start.sh /usr/local/bin/

RUN chmod u+x /usr/local/bin/start.sh
EXPOSE 80
ENTRYPOINT [ "start.sh" ]
