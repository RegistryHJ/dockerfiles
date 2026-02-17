# vim:set ft=dockerfile:
FROM debian:bullseye-slim

LABEL maintainer="RegistryHJ (https://github.com/RegistryHJ)"

ARG DEBIAN_FRONTEND=noninteractive

RUN \
  set -eux; \
  apt-get update && \
  apt-get install -y --no-install-recommends ca-certificates && \
  printf "%s\n" \
  "deb https://ftp.kaist.ac.kr/debian bullseye main" \
  "deb https://ftp.kaist.ac.kr/debian bullseye-updates main" \
  "deb https://ftp.kaist.ac.kr/debian-security bullseye-security main" \
  > /etc/apt/sources.list && \
  apt-get update && \
  apt-get upgrade -y && \
  apt-get install -y --no-install-recommends tzdata && \
  ln -sf /usr/share/zoneinfo/Asia/Seoul /etc/localtime && \
  rm -rf /var/lib/apt/lists/*

ENV LANG=C.UTF-8

CMD ["/bin/bash"]