# FROM alpine:3.20

# COPY ./html/index.php /var/www/localhost/htdocs/

# RUN apk update && \
#      apk add --no-cache apache2 php$phpverx-apache2 && \
#      addgroup -g 1000 -S apache2 && \
#      adduser -S -D -H -u 1000 -h /etc/apache2/ -s /sbin/nologin -g apache2 apache2 && \
#      mkdir -p /app /etc/apache2 /var/www /var/log/apache2 /run/apache2 && \
#      chown -R apache2:apache2 /app && \
#      chown -R apache2:apache2 /etc/apache2 && \
#      chown -R apache2:apache2 /var/www/ && \
#      chown -R apache2:apache2 /var/log/apache2 && \
#      chown -R apache2:apache2 /run/apache2 


# USER apache2

# RUN sed -i 's/:80/:8080/g' /etc/apache2/httpd.conf

# CMD ["httpd", "-D", "FOREGROUND"]


FROM alpine:3.20

COPY ./html/index.php /var/www/localhost/htdocs/

RUN apk update && \
    apk add --no-cache apache2 php$phpverx-apache2 && \
    # addgroup -g 1000 -S apache2 && \
    # adduser -S -D -H -u 1000 -h /etc/apache2/ -s /sbin/nologin -g apache2 apache2 && \
    # mkdir -p /app /etc/apache2 /var/www /var/log/apache2 /run/apache2 && \
    # chown -R apache2:apache2 /app && \
    # chown -R apache2:apache2 /etc/apache2 && \
    # chown -R apache2:apache2 /var/www/ && \
    # chown -R apache2:apache2 /var/log/apache2 && \
    # chown -R apache2:apache2 /run/apache2 && \
    sed -i 's/Listen 80/Listen 8080/g' /etc/apache2/httpd.conf

# USER apache2

CMD ["httpd", "-D", "FOREGROUND"]



# FROM php:8.2-apache

# COPY ./html/index.php /var/www/localhost/htdocs


# RUN sed -i 's/:80/:8080/g' /etc/apache2/httpd.conf
