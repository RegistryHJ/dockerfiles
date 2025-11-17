# vim:set ft=dockerfile:
FROM debian:trixie-slim

LABEL maintainer="RegistryHJ (https://github.com/RegistryHJ)"

ARG DEBIAN_FRONTEND=noninteractive

RUN \
  set -eux; \
  apt-get update && \
  apt-get install -y --no-install-recommends ca-certificates && \
  printf "%s\n" \
  "Types: deb" \
  "URIs: https://ftp.kaist.ac.kr/debian" \
  "Suites: trixie trixie-updates" \
  "Components: main" \
  "Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg" \
  "" \
  "Types: deb" \
  "URIs: https://ftp.kaist.ac.kr/debian-security" \
  "Suites: trixie-security" \
  "Components: main" \
  "Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg" \
  > /etc/apt/sources.list.d/debian.sources && \
  apt-get update && \
  apt-get upgrade -y && \
  apt-get install -y --no-install-recommends tzdata && \
  ln -sf /usr/share/zoneinfo/Asia/Seoul /etc/localtime && \
  rm -rf /var/lib/apt/lists/*

ENV LANG=C.UTF-8

CMD ["/bin/bash"]