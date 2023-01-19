FROM nginx:latest

RUN mv /etc/nginx/conf.d/default.conf /etc/nginx/conf.d/default._conf
ADD ./etc/custom.conf /etc/nginx/conf.d/default.conf

WORKDIR /var/www/