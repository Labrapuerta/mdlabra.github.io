# mdlabra.github.io

This is a static GitHub Pages site with no build dependencies.

## Local preview

Docker Compose runs the site with the same browser-ready HTML, CSS, JavaScript,
and assets that GitHub Pages serves. Packages stay inside the container.

```bash
docker compose up -d
```

Open <http://localhost:8000>. File changes appear immediately because the site
directory is mounted read-only inside the container.

Use a different local port when port 8000 is unavailable:

```bash
SITE_PORT=8080 docker compose up -d
```

Stop the preview environment with:

```bash
docker compose down
```
