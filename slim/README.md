# Slim Dockerfiles

Debian Slim Multi-Architecture Dockerfiles.

[**DockerHub Repository**](https://hub.docker.com/r/registryhj/slim)

<br />

## Features

- **APT Repository Mirror** (`KAIST MIRROR`)
- **Locale Configuration** (`LANG=C.UTF-8`)
- **Timezone Setup** (`Asia/Seoul`)
- **Optimized Package Installation and Caching**

<br />

## Supported Tags

- [**`latest`**](https://hub.docker.com/repository/docker/registryhj/slim/tags?name=latest), [**`trixie`**](https://hub.docker.com/repository/docker/registryhj/slim/tags?name=trixie) - Debian v13 Trixie (Latest)
- [**`bookworm`**](https://hub.docker.com/repository/docker/registryhj/slim/tags?name=bookworm) - Debian v12 Bookworm
- [**`bullseye`**](https://hub.docker.com/repository/docker/registryhj/slim/tags?name=bullseye) - Debian v11 Bullseye (LTS)

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
docker exec -it <container_name> bash
```

<br />

## Supported Architectures

<table border="1">
  <thead>
    <tr>
      <th align="left">Tags</th>
      <th align="left">Architectures</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>latest</code>, <code>trixie</code></td>
      <td><code>linux/amd64</code>, <code>linux/arm64</code>, <code>linux/ppc64le</code>, <code>linux/riscv64</code>, <code>linux/s390x</code></td>
    </tr>
    <tr>
      <td><code>bookworm</code></td>
      <td><code>linux/amd64</code>, <code>linux/arm64</code>, <code>linux/mips64le</code>, <code>linux/ppc64le</code>, <code>linux/s390x</code></td>
    </tr>
    <tr>
      <td><code>bullseye</code></td>
      <td><code>linux/amd64</code>, <code>linux/arm64</code></td>
    </tr>
  </tbody>
</table>

> **Note:** `bullseye` is currently under LTS support (until August 31, 2026) and
> supports `linux/amd64` and `linux/arm64` architectures in this image.
> For more information, see: https://wiki.debian.org/LTS

<br />

## Contact

**For more information, visit:**

- **Maintainer's GitHub:** https://github.com/RegistryHJ

<br />

---

Copyright © 2025 RegistryHJ
