# Alpine Linux Dockerfiles

Alpine Linux Multi-Architecture Dockerfiles.

[**DockerHub Repository**](https://hub.docker.com/r/registryhj/alpine)

<br />

## Features

- **Locale Configuration** (`LANG=C.UTF-8`)
- **Timezone Setup** (`Asia/Seoul`)
- **Optimized Package Installation and Caching**

<br />

## Supported Tags

- [**`latest`**](https://hub.docker.com/repository/docker/registryhj/alpine/tags?name=latest), [**`3.23`**](https://hub.docker.com/repository/docker/registryhj/alpine/tags?name=3.23) - Alpine Linux v3.23
- [**`3.22`**](https://hub.docker.com/repository/docker/registryhj/alpine/tags?name=3.22) - Alpine Linux v3.22
- [**`3.21`**](https://hub.docker.com/repository/docker/registryhj/alpine/tags?name=3.21) - Alpine Linux v3.21
- [**`3.20`**](https://hub.docker.com/repository/docker/registryhj/alpine/tags?name=3.29) - Alpine Linux v3.20

<br />

## How to use

**Navigate to version directory:**

```
cd <version_directory>
```

**Build the image:**

```
docker buildx build -t <image_name>:<tag_name> .
```

**Run container in background:**

```
docker run -d -it --name <container_name> <image_name>:<tag_name>
```

**Container shell access:**

```
docker exec -it <container_name> sh
```

<br />

## Supported Architectures

- `linux/amd64`
- `linux/arm64`
- `linux/ppc64le`
- `linux/riscv64`
- `linux/s390x`

<br />

## Contact

**For more information, visit:**

- **Maintainer's GitHub:** https://github.com/RegistryHJ

<br />

---

Copyright © 2025 RegistryHJ
