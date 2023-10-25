FROM alpine:latest

RUN apk --no-cache add apache2

EXPOSE 80

ADD website.tar.gz /var/www/html/

ENTRYPOINT [ "/usr/sbin/httpd" ]

CMD [ "-D", "FOREGROUND" ]