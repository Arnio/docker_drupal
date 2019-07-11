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
                    php-curl && \
    yum  -y clean all

RUN sed -i -e 's/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/g' /etc/php.ini && \
    curl -sS https://getcomposer.org/installer -o composer-setup.php && \
    php composer-setup.php --install-dir=/usr/local/bin --filename=composer 

COPY ./default /etc/nginx/sites-available/default
COPY ./start.sh /usr/local/bin/

RUN chmod u+x /usr/local/bin/start.sh
EXPOSE 80 
ENTRYPOINT [ "start.sh" ]