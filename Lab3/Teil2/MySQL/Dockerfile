# syntax=docker/dockerfile:1
FROM debian:jessie
RUN apt-get update

RUN apt install -y --force-yes --no-install-recommends wget lsb-release

RUN wget http://repo.mysql.com/mysql-apt-config_0.8.9-1_all.deb
RUN dpkg -i mysql-apt-config_0.8.9-1_all.deb

RUN echo "mysql-server mysql-server/root_password password somewordpress" | debconf-set-selections
RUN echo "mysql-server mysql-server/root_password_again password somewordpress" | debconf-set-selections

RUN apt install -y --force-yes --no-install-recommends mysql-server

RUN sed -i "s/.*bind-address.*/bind-address = 0.0.0.0/" /etc/mysql/my.cnf

VOLUME ["/var/lib/mysql/"]

expose 3306
expose 33060

CMD service mysql start && mysql --user=root --password=somewordpress -e "CREATE USER 'wordpress'@'%' IDENTIFIED BY 'wordpress';" || true && \
mysql --user=root --password=somewordpress -e "CREATE DATABASE IF NOT EXISTS wordpress;" && \
mysql --user=root --password=somewordpress -e "GRANT all privileges ON wordpress.* TO 'wordpress'@'%';" \
mysql --user=root --password=somewordpress -e "flush privileges;" && \
mysqld
