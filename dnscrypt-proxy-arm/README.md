# dnscrypt-proxy-arm

dnscrypt-proxy 2 on an ARM base image

## usage

```
docker create \
--name=dnscrypt-proxy \
-p 0.0.0.0:53:5353/udp \
-p 0.0.0.0:53:5353 \
-v </path to dnscrypt-proxy.toml>:/config/dnscrypt-proxy.toml \
dnscrypt-proxy-arm
```

note: 0.0.0.0 is required in front of the ports due to a [weird docker UDP](https://github.com/moby/moby/issues/11998) [iptables issue](https://github.com/moby/moby/issues/8795).