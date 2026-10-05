FROM ubuntu:24.04
WORKDIR /tmp

ENV DEBIAN_FRONTEND=noninteractive
RUN \
    apt-get -qq -y update && \
    apt-get -qq -y install --no-install-recommends \
      ca-certificates curl gpg lsb-release

## install openresty
RUN curl -sSL https://openresty.org/package/pubkey.gpg | gpg --dearmor -o /usr/share/keyrings/openresty.gpg
RUN echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/openresty.gpg] https://openresty.org/package/ubuntu $(lsb_release -sc) main" \
    | tee /etc/apt/sources.list.d/openresty.list > /dev/null
RUN apt-get -qq -y update && \
    apt-get -qq -y install --no-install-recommends openresty openresty-opm

#RUN git clone https://github.com/nemethhh/lua-resty-ja4
#RUN cp -r lua-resty-ja4/lib/resty/* /usr/share/lua/5.1/resty/
RUN opm get nemethhh/lua-resty-ja4

#RUN \
#    ln -sf /dev/stdout /var/log/nginx/access.log && \
#    ln -sf /dev/stderr /var/log/nginx/error.log

#COPY nginx/ssl /etc/nginx/ssl
#COPY nginx/nginx.conf /etc/nginx/conf.d/nginx.conf
COPY nginx/ssl /etc/openresty/ssl
COPY nginx/openresty.conf /etc/openresty/nginx.conf

#CMD ["nginx", "-g", "daemon off;"]
CMD ["openresty", "-g", "daemon off;"]
