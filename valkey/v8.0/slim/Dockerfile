# vim:set ft=dockerfile:
FROM registryhj/slim:trixie AS base
FROM base AS build

LABEL maintainer="RegistryHJ (https://github.com/RegistryHJ)"

ENV VALKEY_VERSION=8.0.6
ENV VALKEY_DOWNLOAD_SHA=f8d15c257a3619e0e42e68998e9dc16536009d257662efa4c62ef7d08a71b0dd

ADD "https://github.com/valkey-io/valkey/archive/refs/tags/${VALKEY_VERSION}.tar.gz" /valkey.tar.gz

RUN set -eux; \
	apt-get update; \
	apt-get install -y --no-install-recommends \
		dpkg-dev gcc libc6-dev libssl-dev libsystemd-dev make; \
	rm -rf /var/lib/apt/lists/*; \
  echo "$VALKEY_DOWNLOAD_SHA *valkey.tar.gz" | sha256sum -c -; \
	mkdir -p /usr/src/valkey; \
	tar -xzf valkey.tar.gz -C /usr/src/valkey --strip-components=1; \
	rm valkey.tar.gz; \
	grep -E '^ *createBoolConfig[(]"protected-mode",.*, *1 *,.*[)],$' /usr/src/valkey/src/config.c; \
	sed -ri 's!^( *createBoolConfig[(]"protected-mode",.*, *)1( *,.*[)],)$!\10\2!' /usr/src/valkey/src/config.c; \
	grep -E '^ *createBoolConfig[(]"protected-mode",.*, *0 *,.*[)],$' /usr/src/valkey/src/config.c; \
	gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)"; \
	extraJemallocConfigureFlags="--build=$gnuArch"; \
	dpkgArch="$(dpkg --print-architecture)"; \
	case "${dpkgArch##*-}" in \
		amd64 | i386 | x32) extraJemallocConfigureFlags="$extraJemallocConfigureFlags --with-lg-page=12";; \
		*) extraJemallocConfigureFlags="$extraJemallocConfigureFlags --with-lg-page=16";; \
	esac; \
	extraJemallocConfigureFlags="$extraJemallocConfigureFlags --with-lg-hugepage=21"; \
	grep -F 'cd jemalloc && ./configure ' /usr/src/valkey/deps/Makefile; \
	sed -ri 's!cd jemalloc && ./configure !&'"$extraJemallocConfigureFlags"' !' /usr/src/valkey/deps/Makefile; \
	grep -F "cd jemalloc && ./configure $extraJemallocConfigureFlags " /usr/src/valkey/deps/Makefile; \
	export BUILD_TLS=yes; \
	export USE_SYSTEMD=yes; \
	make -C /usr/src/valkey -j "$(nproc)" all; \
	make -C /usr/src/valkey install; \
	serverMd5="$(md5sum /usr/local/bin/valkey-server | cut -d' ' -f1)"; export serverMd5; \
	find /usr/local/bin/valkey* -maxdepth 0 \
		-type f -not -name valkey-server \
		-exec sh -eux -c ' \
			md5="$(md5sum "$1" | cut -d" " -f1)"; \
			test "$md5" = "$serverMd5"; \
		' -- '{}' ';' \
		-exec ln -svfT 'valkey-server' '{}' ';'; \
	echo '{"spdxVersion":"SPDX-2.3","SPDXID":"SPDXRef-DOCUMENT","name":"valkey-server-sbom","packages":[{"name":"valkey-server","versionInfo":"7.2.11","SPDXID":"SPDXRef-Package--valkey-server","externalRefs":[{"referenceCategory":"PACKAGE-MANAGER","referenceType":"purl","referenceLocator":"pkg:generic/valkey-server@7.2.11?os_name=debian&os_version=trixie"}],"licenseDeclared":"BSD-3-Clause"}]}' > /usr/local/valkey.spdx.json

FROM base

RUN set -eux; \
	groupadd -r -g 999 valkey; \
	useradd -r -g valkey -u 999 valkey

RUN set -eux; \
	apt-get update; \
	apt-get install -y --no-install-recommends \
		tzdata libssl3t64; \
	rm -rf /var/lib/apt/lists/*

COPY --from=build /usr/local /usr/local

RUN mkdir /data && \
	chown valkey:valkey /data && \
	mkdir -p /run/valkey && \
	chown valkey:valkey /run/valkey && \
	valkey-cli --version && \
	valkey-server --version

WORKDIR /data

COPY --chmod=755 docker-entrypoint.sh /usr/local/bin/
ENTRYPOINT ["docker-entrypoint.sh"]

EXPOSE 6379
CMD ["valkey-server"]