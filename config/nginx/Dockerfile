FROM alpine

ARG PROJECT_DOMAIN

RUN apk add --update nginx
RUN rm -rf /var/cache/apk/* && rm -rf /tmp/*

ADD nginx.conf /etc/nginx/
ADD project.conf /etc/nginx/conf.d/

RUN sed -i 's#__PROJECT_DOMAIN__#'"${PROJECT_DOMAIN}"'#g' /etc/nginx/conf.d/project.conf
RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf

RUN adduser -D -g '' -G www-data www-data

CMD ["nginx"]

EXPOSE 80
EXPOSE 443