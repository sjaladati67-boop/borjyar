# Borjyar

Minimal Docker Compose Hello World, ready for deployment with a self-hosted GitHub Actions runner.

## Deploy locally on the runner host

The runner needs Docker and Docker Compose access, and write access to `/opt/apps/borjyar`.

```bash
sudo mkdir -p /opt/apps/borjyar
sudo chown -R "$(id -un):$(id -gn)" /opt/apps/borjyar
git clone https://github.com/sjaladati67-boop/borjyar.git /opt/apps/borjyar
cd /opt/apps/borjyar
docker compose up -d
curl -f http://127.0.0.1:18081/
```

If the directory already exists, do not clone over it; pull or copy the repository files instead. GitHub Actions deploys on pushes to `main` using a self-hosted runner installed **on the target server**.

The app listens only on `127.0.0.1:18081`, ready for an existing reverse proxy. No public port or existing Nginx configuration is changed.

## Operations

```bash
cd /opt/apps/borjyar
docker compose ps
docker compose logs --tail=100
docker compose down
```
