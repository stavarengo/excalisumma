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

ExcaliSumma started as a fork of [ZimengXiong/ExcaliDash](https://github.com/ZimengXiong/ExcaliDash) in October 2026 and is developed independently since.

ExcaliSumma is licensed under the GNU Lesser General Public License v3.0.
