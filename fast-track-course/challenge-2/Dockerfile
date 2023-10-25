FROM debian:latest

RUN apt-get update && apt-get install -y apache2


# Set Apache environment variables (can be in a separate ENV for clarity)
ENV APACHE_RUN_USER=www-data \
    APACHE_RUN_GROUP=www-data \
    APACHE_RUN_DIR=/var/run/apache2 \
    APACHE_PID_FILE=/var/run/apache2/apache2.pid \
    APACHE_LOCK_DIR=/var/lock/apache2 \
    APACHE_LOG_DIR=/var/log/apache2 \
    LANG=C

EXPOSE 80

ADD website.tar.gz /var/www/html/

ENTRYPOINT [ "/usr/sbin/apache2" ]

CMD [ "-D", "FOREGROUND" ]