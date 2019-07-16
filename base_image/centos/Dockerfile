FROM centos:7
RUN yum -y install yum-plugin-fastestmirror httpd epel-release && \
    yum -y install http://rpms.remirepo.net/enterprise/remi-release-7.rpm && \
    yum-config-manager --enable remi-php73 

RUN yum install -y nginx \
                    curl \
                    git \
                    unzip \
                    php \
                    php-fpm \
                    php-common \
                    php-opcache \
                    php-mbstring \
                    php-xmlrpc \
                    php-soap \
                    php-gd \
                    php-xml \
                    php-intl \
                    php-mysql \
                    php-cli \
                    php-tidy \
                    php-recode \
                    php-zip \
                    php-xml \
                    php-curl && \
    yum  -y clean all

RUN sed -i -e 's/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/g' /etc/php.ini && \
    mkdir -p /var/www/html /var/run/php-fpm/ && \
    curl -sS https://getcomposer.org/installer -o composer-setup.php && \
    php composer-setup.php --install-dir=/usr/local/bin --filename=composer 

COPY ./nginx.conf /etc/nginx/nginx.conf
COPY ./default /etc/nginx/conf.d/default.conf
COPY ./www.conf /etc/php-fpm.d/www.conf
COPY ./start.sh /usr/local/bin/
COPY ./info.php /var/www/html/index.php

RUN chmod u+x /usr/local/bin/start.sh
EXPOSE 80 
ENTRYPOINT [ "start.sh" ]