# Termix

Self-hosted web terminal powered by [Termix](https://github.com/lukegus/termix) and [Apache Guacamole](https://guacamole.apache.org/).

## Prerequisites

- Docker
- Docker Compose

## Quick Start

```bash
docker compose up -d
```

Access the web terminal at `http://localhost:8080`.

## Services

| Service | Image | Port |
|---------|-------|------|
| termix  | `ghcr.io/lukegus/termix:2.7.1` | 8080 |
| guacd   | `guacamole/guacd:1.6.0` | internal |

## Stop

```bash
docker compose down
```

```bash
docker compose down
```

## Updating

Images in `docker-compose.yml` are pinned to specific versions for stability:

```yaml
image: ghcr.io/lukegus/termix:2.7.1
image: guacamole/guacd:1.6.0
```

To update to a newer version:

1. Check the latest available tags:
   - [Termix releases]([https://github.com/lukegus/termix/pkgs/container/termix](https://github.com/Termix-SSH/Termix/releases])
   - [Guacd releases](https://hub.docker.com/r/guacamole/guacd/tags)

2. Update the image tag in `docker-compose.yml`:
   ```yaml
   image: ghcr.io/lukegus/termix:<new-version>
   image: guacamole/guacd:<new-version>
   ```

3. Pull the new images and recreate containers:
   ```bash
   docker compose pull
   docker compose up -d
   ```

4. Remove old images (optional):
   ```bash
   docker image prune
   ```

> **Note:** Always back up the `termix-data` volume before major version upgrades.

## Data

Persistent data is stored in the `termix-data` volume.

## License

MIT
