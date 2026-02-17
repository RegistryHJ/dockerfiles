# Valkey Dockerfiles

Valkey Multi-Architecture Dockerfiles.

[**DockerHub Repository**](https://hub.docker.com/r/registryhj/valkey)

<br />

## Features

- **Alpine, Slim Image Based** ([`registryhj/alpine`](https://hub.docker.com/r/registryhj/alpine), [`registryhj/slim`](https://hub.docker.com/r/registryhj/slim))
- **Optimized Package Installation and Caching**

<br />

## Supported Tags

- [**`latest`**](https://hub.docker.com/repository/docker/registryhj/valkey/tags?name=latest), [**`9.0`**](https://hub.docker.com/repository/docker/registryhj/valkey/tags?name=9.0) - Valkey v9.0 Slim (v9.0.2, Latest)
- [**`9.0-alpine`**](https://hub.docker.com/repository/docker/registryhj/valkey/tags?name=9.0-alpine) - Valkey v9.0 Alpine (v9.0.2)
- [**`8.1`**](https://hub.docker.com/repository/docker/registryhj/valkey/tags?name=8.1) - Valkey v8.1 Slim (v8.1.5)
- [**`8.1-alpine`**](https://hub.docker.com/repository/docker/registryhj/valkey/tags?name=8.1-alpine) - Valkey v8.1 Alpine (v8.1.5)
- [**`8.0`**](https://hub.docker.com/repository/docker/registryhj/valkey/tags?name=8.0) - Valkey v8.0 Slim (v8.0.6)
- [**`8.0-alpine`**](https://hub.docker.com/repository/docker/registryhj/valkey/tags?name=8.0-alpine) - Valkey v8.0 Alpine (v8.0.6)
- [**`7.2`**](https://hub.docker.com/repository/docker/registryhj/valkey/tags?name=7.2) - Valkey v7.2 Slim (v7.2.11)
- [**`7.2-alpine`**](https://hub.docker.com/repository/docker/registryhj/valkey/tags?name=7.2-alpine) - Valkey v7.2 Alpine (v7.2.11)

<br />

## How to use

**Navigate to version directory:**

```
cd <version_directory>
```

**Build the image:**

```
docker buildx build -t <image_name>:<tag_name>
```

**Run container in background:**

```
docker run -d \
    --name <container_name> \
    -p 6379:6379 \
    registryhj/valkey:<tag_name> \
    valkey-server \
    --requirepass <password>
```

or If you want to set persistent storage:

```
docker run -d \
    --name <container_name> \
    -p 6379:6379 \
    registryhj/valkey:<tag_name> \
    valkey-server \
    --requirepass <password> \
    --save 60 1 \
    --loglevel warning
```

**Container Valkey CLI access:**

```
docker exec -it <container_name> valkey-cli
```

<br />

## Supported Architectures

- `linux/amd64`
- `linux/arm64`

<br />

## Contact

**For more information, visit:**

- **Maintainer's GitHub:** https://github.com/RegistryHJ

<br />

---

Copyright © 2026 RegistryHJ
