FROM mysql:latest

USER root

RUN chmod 777 /var/lib/mysql

COPY ./my.cnf /etc/mysql/conf.d/

EXPOSE 3306