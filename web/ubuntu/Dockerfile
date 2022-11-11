FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update
RUN apt-get install -y software-properties-common
RUN apt-get install -y mc nano curl nginx php php-fpm php-common php-mysql php-gd php-cli php-curl php-json php-cgi php-gd php-zip php-mbstring php-xml php-xmlrpc php-intl php-xdebug php-imap
RUN apt-get purge -y apache2

COPY ./default /etc/nginx/sites-available/
COPY ./php.ini /etc/php/7.2/fpm
COPY ./xdebug.ini /etc/php/7.2/mods-available/

RUN useradd -G www-data,root -u 501 -d /home/ec ec
RUN ln -s /var/www/html/yii /usr/bin/yii

CMD service php7.2-fpm start && nginx -g "daemon off;"

EXPOSE 80
EXPOSE 9001
