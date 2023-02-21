FROM alpine:3.17
MAINTAINER Rezky <yurandarezky@atmaluhur.ac.id>

RUN apk update &&\
		apk add --no-cache\
		nginx \
		php81\
		php81-session\
		php81-fpm\
		php81-cli\
		php81-opcache\
		php81-gd\
		php81-mysqli\
		php81-zlib\
		php81-curl\
		php81-json\
		php81-dom\
		php81-exif\
		php81-fileinfo\
		php81-mbstring\
		php81-zip\
		php81-iconv\
		php81-intl\
		php81-pecl-imagick\
		php81-dev\
		php81-pear\
		gcc\
		libc-dev\
		make\
		libnsl\
		libaio\
		unzip\
		wget &&\
		wget https://github.com/tabung/php-oci-instant-client/raw/main/oracle-instantclient/instantclient-basic-linux.x64-11.2.0.4.0.zip -O /tmp/instantclient-basic-linux.x64-11.2.0.4.0.zip &&\
		wget https://github.com/tabung/php-oci-instant-client/raw/main/oracle-instantclient/instantclient-sdk-linux-x86-64-11.2.0.2.0.zip -O /tmp/instantclient-sdk-linux.x64-11.2.0.4.0.zip &&\
 		unzip /tmp/instantclient-basic-linux.x64-11.2.0.4.0.zip -d /usr/local/ &&\
  	unzip /tmp/instantclient-sdk-linux.x64-11.2.0.4.0.zip  -d /usr/local/ &&\
		ln -sf /usr/local/instantclient_11_2/ /usr/local/instantclient &&\
		ln -s /usr/local/instantclient/libclntsh.so.11.1 /usr/local/instantclient/libclntsh.so &&\
		ln -s /usr/local/instantclient/libocci.so.11.1 /usr/local/instantclient/libocci.so &&\
		ln -s /usr/lib/libnsl.so.3 /usr/lib/libnsl.so.1 &&\
		echo 'instantclient,/usr/local/instantclient' | pecl install oci8 &&\
		echo 'extension=oci8.so' > /etc/php81/conf.d/oci8.ini &&\
		apk del wget unzip make gcc &&\
		rm -r /tmp/*
		
COPY ./www.conf /etc/php81/php-fpm.d/www.conf
COPY ./default.conf /etc/nginx/http.d/default.conf

CMD php-fpm81 && nginx -g "daemon off;"
