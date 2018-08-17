FROM arm32v7/debian:9.5

RUN set -x && \
    apt-get update && \
    apt-get install -y curl # --no-install-recommends

ENV DNSCRYPT_PROXY_VERSION 2.0.16
ENV DNSCRYPT_PROXY_ARCH linux_arm
ENV DNSCRYPT_PROXY_DOWNLOAD_URL https://github.com/jedisct1/dnscrypt-proxy/releases/download/${DNSCRYPT_PROXY_VERSION}/dnscrypt-proxy-${DNSCRYPT_PROXY_ARCH}-${DNSCRYPT_PROXY_VERSION}.tar.gz

RUN set -x && \
    mkdir -p /opt/dnscrypt-proxy/empty && \
    cd /opt/dnscrypt-proxy && \
    curl -sSL $DNSCRYPT_PROXY_DOWNLOAD_URL -o dnscrypt-proxy.tar.gz && \
    tar xzf dnscrypt-proxy.tar.gz --strip-components=1 && \
    rm -f dnscrypt-proxy.tar.gz

ADD config /config
EXPOSE 5353/tcp 5353/udp

CMD ["/opt/dnscrypt-proxy/dnscrypt-proxy", "-config", "/config/dnscrypt-proxy.toml"]
