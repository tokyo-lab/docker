FROM alpine:latest

RUN apk --no-cache add apache2

EXPOSE 80

ADD website.tar.gz /var/www/localhost/htdocs/

ENTRYPOINT [ "/usr/sbin/httpd" ]

CMD [ "-D", "FOREGROUND" ]