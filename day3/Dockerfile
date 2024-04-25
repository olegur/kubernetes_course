FROM alpine:latest
RUN apk update && apk add nginx unzip

#securitehh more better?
RUN adduser -D -g 'www' www
RUN mkdir /www

#add nginx template config
ADD --chown=www:root src/nginx-example.conf /etc/nginx/nginx.conf

#add src files and move into place
ADD src/startbootstrap-sb-admin-gh-pages.zip /tmp/
RUN unzip /tmp/startbootstrap-sb-admin-gh-pages.zip -d "/tmp/"
RUN mv /tmp/startbootstrap-sb-admin-gh-pages/* /www/

#correct rights after files are placed
#RUN chown -R www:www /var/lib/nginx
RUN chown -R www:www /www && chmod -R 755 /www
#RUN chown -R www:www /var/cache/nginx
RUN chown -R www:www /var/lib/nginx
RUN chown -R www:www /var/log/nginx
#RUN chown -R www:www /etc/nginx/conf.d
#RUN mkdir /run/nginx
RUN touch /run/nginx/nginx.pid
RUN chown -R www:www /run/nginx

#change to www user
USER www

EXPOSE 8081

#run nginx
CMD ["/usr/sbin/nginx", "-g", "daemon off;"]

#EXPOSE 8081

