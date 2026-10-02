FROM ubuntu:24.04
WORKDIR /tmp

ENV DEBIAN_FRONTEND=noninteractive
RUN \
    apt-get -qq -y update && \
    apt-get -qq -y install git nginx-full lua-resty-core

RUN git clone https://github.com/nemethhh/lua-resty-ja4
RUN cp -r lua-resty-ja4/lib/resty/* /usr/share/lua/5.1/resty/

RUN \
    ln -sf /dev/stdout /var/log/nginx/access.log && \
    ln -sf /dev/stderr /var/log/nginx/error.log

CMD ["nginx", "-g", "daemon off;"]
