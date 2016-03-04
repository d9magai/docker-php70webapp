FROM centos
MAINTAINER d9magai

RUN yum update -y && yum install -y epel-release && yum clean all
RUN rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
RUN yum update -y \
    && yum install -y \
    httpd \
    httpd-devel \
    php70 \
    php70-php \
    php70-php-devel \
    php70-php-gd \
    php70-php-pdo \
    php70-php-mbstring \
    php70-php-mcrypt \
    php70-php-mysqlnd \
    php70-php-opcache \
    php70-php-xml \
    php70-php-pecl-memcached \
    && yum clean all

RUN sed -i -e "s/;date.timezone *=.*$/date.timezone = Asia\/Tokyo/" /etc/opt/remi/php70/php.ini

ENV WEBAPP_ROOT /webapp
ENV PATH /opt/remi/php70/root/usr/bin:/opt/remi/php70/root/usr/sbin${PATH:+:${PATH}}
ENV LD_LIBRARY_PATH /opt/remi/php70/root/usr/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
ENV MANPATH /opt/remi/php70/root/usr/share/man:${MANPATH}

ADD ./httpd.conf /etc/httpd/conf/httpd.conf

EXPOSE 80

CMD ["/usr/sbin/httpd","-D","FOREGROUND"]

