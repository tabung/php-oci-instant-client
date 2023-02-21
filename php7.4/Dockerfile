FROM alpine:3.15
MAINTAINER Rezky <yurandarezky@atmaluhur.ac.id>

RUN apk update &&\
		apk add --no-cache \
		nginx \
		php7 \
		php7-session \
		php7-fpm \
		php7-cli \
		php7-opcache \
		php7-gd \
		php7-mysqli \
		php7-zlib \
		php7-curl \
		php7-json \
		php7-dom \
		php7-exif \
		php7-fileinfo \
		php7-mbstring \
		php7-zip \
		php7-iconv \
		php7-intl \
		php7-pecl-imagick \
		php7-dev \
		php7-pear \
		gcc \
		libc-dev \
		make \
		libnsl \ 
		libaio \
		unzip \
		wget && \
		wget https://github.com/tabung/php-oci-instant-client/raw/main/oracle-instantclient/instantclient-basic-linux.x64-11.2.0.4.0.zip -O /tmp/instantclient-basic-linux.x64-11.2.0.4.0.zip && \
    wget https://github.com/tabung/php-oci-instant-client/raw/main/oracle-instantclient/instantclient-sdk-linux-x86-64-11.2.0.2.0.zip -O /tmp/instantclient-sdk-linux.x64-11.2.0.4.0.zip && \
    unzip /tmp/instantclient-basic-linux.x64-11.2.0.4.0.zip -d /usr/local/ && \
    unzip /tmp/instantclient-sdk-linux.x64-11.2.0.4.0.zip -d /usr/local/ &&\
		ln -s /usr/local/instantclient_11_2 /usr/local/instantclient && \
		ln -s /usr/local/instantclient/libclntsh.so.* /usr/local/instantclient/libclntsh.so && \
		ln -s /usr/local/instantclient/libocci.so.* /usr/local/instantclient/libocci.so && \
		ln -s /usr/lib/libnsl.so.2 /usr/lib/libnsl.so.1 && \
		echo 'instantclient,/usr/local/instantclient' | pecl install oci8-2.2.0 && \
		echo 'extension=oci8.so' > /etc/php7/conf.d/oci8.ini && \
		apk del wget make autoconf g++ unzip && \
		rm -rf /var/lib/apt/lists/* /var/lib/log/* /tmp/* /var/tmp/*

COPY ./www.conf /etc/php7/php-fpm.d/www.conf
COPY ./default.conf /etc/nginx/http.d/default.conf

CMD php-fpm7 && nginx -g "daemon off;"
