# Local preview

This repository is a static GitHub Pages site. Preview it through Docker Compose
instead of installing packages on the host.

## Agent workflow

1. Ensure Docker is available. If its daemon is stopped on macOS, run
   `open -a Docker` and wait until `docker info` succeeds.
2. Start the preview with `docker compose up -d --wait`.
3. Edit the site files normally. The site directory is mounted read-only, so
   changes appear at <http://localhost:8000> without rebuilding or restarting.
4. Verify the affected pages and assets with `curl --fail --silent
   http://localhost:8000/<path>`. Run `docker compose ps` and inspect
   `docker compose logs site` if the preview is unhealthy.
5. Show the result by giving the local URL, or run `open http://localhost:8000`
   when a browser preview is appropriate.

## Lifecycle

`docker compose up -d` runs a detached container. It continues after the agent
session ends. Stop it explicitly with `docker compose down`. It also stops if
Docker Desktop or the computer stops; automatic startup after a host restart is
not configured.
