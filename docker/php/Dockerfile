FROM centos:7

# update yum
RUN yum -y update
RUN yum -y install yum-utils
RUN yum clean all

RUN yum -y install epel-release
RUN yum -y groupinstall "Development Tools"
RUN yum -y install wget curl

# install remi repo
RUN wget http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
RUN rpm -Uvh remi-release-7*.rpm
RUN yum-config-manager --enable remi-php72

# install php7
RUN yum -y install \
    php \
    php-cli \
    php-common \
    php-devel \
    php-gd \
    php-json \
    php-mbstring \
    php-mcrypt \
    php-mysqlnd \
    php-opcache \
    php-pdo \
    php-pear.noarch \
    php-pecl-imagick \
    php-process \
    php-xml \
    php-xdebug

# application directory
WORKDIR /app

# install composer
#COPY --from=composer:2.4 /usr/bin/composer /usr/bin/composer
COPY --from=composer:1.8.6 /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_NO_INTERACTION 1
