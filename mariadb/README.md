# MariaDB Dockerfiles

MariaDB Multi-Architecture Dockerfiles.

[**DockerHub Repository**](https://hub.docker.com/r/registryhj/mariadb)

<br />

## Features

- **Slim Image Based** ([`registryhj/slim`](https://hub.docker.com/r/registryhj/slim))
- **Optimized Package Installation and Caching**

<br />

## Supported Tags

- [**`latest`**](https://hub.docker.com/repository/docker/registryhj/mariadb/tags?name=latest), [**`12.2`**](https://hub.docker.com/repository/docker/registryhj/mariadb/tags?name=12.2) - MariaDB v12.2 (v12.2.2, Latest)
- [**`lts`**](https://hub.docker.com/repository/docker/registryhj/mariadb/tags?name=lts), [**`11.8`**](https://hub.docker.com/repository/docker/registryhj/mariadb/tags?name=11.8) - MariaDB v11.8 (v11.8.6, LTS)
- [**`11.4`**](https://hub.docker.com/repository/docker/registryhj/mariadb/tags?name=11.4) - MariaDB v11.4 (v11.4.10)
- [**`10.11`**](https://hub.docker.com/repository/docker/registryhj/mariadb/tags?name=10.11) - MariaDB v10.11 (v10.11.16)
- [**`10.6`**](https://hub.docker.com/repository/docker/registryhj/mariadb/tags?name=10.6) - MariaDB v10.6 (v10.6.25)

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
    -p <port>:3306 \
    -e MARIADB_ROOT_PASSWORD=<password> \
    registryhj/mariadb:<tag_name>
```

or If you want to set `User` and `Database`:

```
docker run -d \
    --name <container_name> \
    -p <port>:3306 \
    -e MARIADB_ROOT_PASSWORD=<password> \
    -e MARIADB_USER=<user> \
    -e MARIADB_PASSWORD=<password> \
    -e MARIADB_DATABASE=<database> \
    registryhj/mariadb:<tag_name>
```

**Container MariaDB Client access:**

```
docker exec -it <container_name> mariadb -u root -p
```

or If you want to set `User` and `Database`:

```
docker exec -it <container_name> mariadb -u <user> -p <database>
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
