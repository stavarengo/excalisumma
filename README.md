# ExcaliSumma

Self-hosted Excalidraw workspaces with collections, real-time collaboration,
sharing, history, backups, and local or OpenID Connect authentication.

![ExcaliSumma dashboard](docs/public/images/workspace.png)

[Self-host Excalidraw with Docker Compose](docs/deploy/docker.md),
or read the documentation in [`docs/`](docs/).

## Quick start

```sh
git clone https://github.com/stavarengo/excalisumma.git
cd excalisumma
docker compose -f docker-compose.prod.yml up -d
```

Open <http://localhost:6767>. Configuration and deployment guidance live in
the [documentation](docs/).

## Why this project

This fork started because I wanted a version of Excalidraw that met my needs, but I couldn't find one that had everything I was looking for in one place.

The goal is to gradually expand its capabilities, covering more use cases and reducing the need for other tools when working with an infinite canvas.

ExcaliSumma started as a fork of [ZimengXiong/ExcaliDash](https://github.com/ZimengXiong/ExcaliDash) in October 2026 and is developed independently since.

ExcaliSumma is licensed under the GNU Lesser General Public License v3.0.
