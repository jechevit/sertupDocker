FROM ubuntu:18.04

RUN apt-get update && apt-get install -y gnupg
RUN groupadd -r mysql && useradd -r -g mysql mysql

#Add the MySQL APT repository & Install necessary programs
RUN apt-get update \
    && apt-get update \
    && apt-get install -y --no-install-recommends perl pwgen

#Install MySQL
RUN apt-get install -y mysql-server \
    && mkdir -p /var/lib/mysql /var/run/mysqld \
    && chown -R mysql:mysql /var/lib/mysql /var/run/mysqld \
    && chmod 777 /var/run/mysqld

#Solve the problem that ubuntu cannot log in from another container
RUN sed -i 's/bind-address/#bind-address/' /etc/mysql/mysql.conf.d/mysqld.cnf

#Install other programs
RUN apt-get install -y nano mc pbzip2 mysql-server
RUN mkdir /home/dump
RUN useradd -G mysql,root -u 501 -d /home/ec ec

CMD ["mysqld","--user","mysql"]

EXPOSE 3306
