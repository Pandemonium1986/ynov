FROM ubuntu:18.04

EXPOSE 80

RUN apt-get update && \
    apt-get install -y \
      nginx \ 
      ca-certificates

RUN ln -sf /dev/stdout /var/log/nginx/access.log && \
    ln -sf /dev/stderr /var/log/nginx/error.log

RUN sed -i '1s/^/daemon off;\n/' /etc/nginx/nginx.conf

COPY html /usr/share/nginx/html/

ENTRYPOINT ["/etc/init.d/nginx", "start"]
