# Juke-Nuke Beta Install Guide

## TrueNAS SCALE quick start

Create the persistent folders:

```bash
sudo mkdir -p /mnt/APP_POOL/Juke-Nuke/{data,config,cache,uploads,backups,logs} && \
sudo chmod -R 770 /mnt/APP_POOL/Juke-Nuke
```

If your application pool is not named `APP_POOL`, change that part of the path first.

The supplied `docker-compose.truenas.yml` expects the media library at:

```text
/mnt/tank/media
```

Change that volume path if your media lives elsewhere.

Start Juke-Nuke:

```bash
git clone https://github.com/christianrobertson36/Juke-Nuke-Beta.git
cd Juke-Nuke-Beta
docker compose -f docker-compose.truenas.yml pull
docker compose -f docker-compose.truenas.yml up -d
```

Open:

```text
http://YOUR-TRUENAS-IP:3105
```

Health check:

```bash
curl -fsS http://127.0.0.1:3105/health
```

## Standard Docker / Dockge

Clone the repo and copy the environment template:

```bash
git clone https://github.com/christianrobertson36/Juke-Nuke-Beta.git
cd Juke-Nuke-Beta
cp .env.example .env
```

Edit `.env` if you need a different port or media path, then run:

```bash
docker compose pull
docker compose up -d
```

Default address:

```text
http://YOUR-SERVER-IP:3105
```

## Updating

```bash
git pull
docker compose pull
docker compose up -d
```

For TrueNAS:

```bash
git pull
docker compose -f docker-compose.truenas.yml pull
docker compose -f docker-compose.truenas.yml up -d
```

## Logs

```bash
docker compose logs --tail=200 juke-nuke
```

## Removing the container

```bash
docker compose down
```

Persistent data and your external media library are not deleted by that command.
