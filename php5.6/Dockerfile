FROM alpine:3.8
MAINTAINER Rezky <yurandarezky@atmaluhur.ac.id>

RUN apk update && \
		apk add --no-cache \
		nginx \
		php5 \
		php5-fpm \
		php5-cli \
		php5-opcache \
		php5-gd \
		php5-mysqli \
		php5-zlib \
		php5-curl \
		php5-json \
		php5-dom \
		php5-exif \
		php5-zip \
		php5-iconv \
		php5-intl \
		php5-dev \
		php5-pear \
		gcc \
		libc-dev \
		make \
		libnsl \
		libaio \
		unzip \
		wget \
		autoconf \
		automake \
		libtool && \
		wget https://github.com/tabung/php-oci-instant-client/raw/main/oracle-instantclient/instantclient-basic-linux.x64-11.2.0.4.0.zip -O /tmp/instant-basic-linux.zip && \
		wget https://github.com/tabung/php-oci-instant-client/raw/main/oracle-instantclient/instantclient-sdk-linux-x86-64-11.2.0.2.0.zip -O /tmp/instant-sdk-linux.zip &&\
		unzip /tmp/instant-basic-linux.zip -d /usr/local/ && \
		unzip /tmp/instant-sdk-linux.zip -d /usr/local/ && \
		ln -s /usr/local/instantclient_11_2 usr/local/instantclient && \
		ln -s /usr/local/instantclient/libclntsh.so.* /usr/local/instantclient/libclntsh.so && \
		ln -s /usr/local/instantclient/libocci.so.* /usr/local/instantclient/libocci.so &&\
		ln -s /usr/lib/libnsl.so.2 /usr/lib/libnsl.so.1 && \
   ln -s /usr/bin/php5 /usr/bin/php && \
		echo 'instantclient,/usr/local/instantclient' | pecl install oci8-2.0.12 && \
		echo 'extension=oci8.so' > /etc/php5/conf.d/oci8.ini && \
		rm -rf /tmp/*

COPY ./default.conf /etc/nginx/conf.d/default.conf 
COPY ./www.conf /etc/php5/fpm.d/www.conf 

CMD mkdir /run/nginx && php-fpm5 && nginx -g "daemon off;"
