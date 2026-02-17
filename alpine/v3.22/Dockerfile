# vim:set ft=dockerfile:
FROM alpine:3.22

LABEL maintainer="RegistryHJ (https://github.com/RegistryHJ)"

RUN \
  set -eux; \
  apk update && \
  apk upgrade && \
  apk add --no-cache tzdata && \
  ln -sf /usr/share/zoneinfo/Asia/Seoul /etc/localtime && \
  rm -rf /var/cache/apk/*

ENV LANG=C.UTF-8

CMD ["/bin/sh"]