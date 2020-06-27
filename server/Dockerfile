# 环境
FROM alpine
ARG BIND_PORT
ARG VHOST_HTTP_PORT
#RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories
RUN apk update && \
    apk add --no-cache wget && \
    apk add --no-cache tar

# frp
WORKDIR /home
RUN wget https://github.com/fatedier/frp/releases/download/v0.33.0/frp_0.33.0_linux_amd64.tar.gz && \
    tar -zxvf frp_0.33.0_linux_amd64.tar.gz && \
    mv frp_0.33.0_linux_amd64 frp
COPY frps.ini ./frp/frps.ini
#RUN envsubst '$VHOST_HTTP_PORT $BIND_PORT' < /home/frp/frps.ini > /home/frp/frps.ini
WORKDIR /home/frp

CMD ./frps -c ./frps.ini