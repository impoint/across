# Dockerfile for trojan-go based alpine
# Copyright (C) 2019 - 2020 Teddysun <i@teddysun.com>
# Reference URL:
# https://github.com/p4gefau1t/trojan-go
# https://github.com/v2ray/v2ray-core
# https://github.com/v2ray/geoip
# https://github.com/v2ray/domain-list-community

FROM alpine:latest
LABEL maintainer="Teddysun <i@teddysun.com>"

COPY trojan-go.sh /root/trojan-go.sh
COPY config.json /etc/trojan-go/config.json
RUN set -ex \
	&& apk add --no-cache tzdata ca-certificates \
	&& chmod +x /root/trojan-go.sh \
	&& /root/trojan-go.sh \
	&& rm -fv /root/trojan-go.sh \
	&& wget -O /usr/bin/geosite.dat https://github.com/v2fly/domain-list-community/releases/latest/download/dlc.dat \
	&& wget -O /usr/bin/geoip.dat https://github.com/v2fly/geoip/releases/latest/download/geoip.dat

VOLUME /etc/trojan-go
ENV TZ=Asia/Shanghai
CMD [ "/usr/bin/trojan-go", "-config", "/etc/trojan-go/config.json" ]
