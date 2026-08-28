# Juke-Nuke Private Beta

Private reviewer build of Juke-Nuke — a self-hosted entertainment centre for TrueNAS/Docker with music, movies/video, photos, karaoke, radio, IPTV, playlists, retro/arcade features, remote control and shared playback state.

> This repository is for invited beta reviewers only. Please do not redistribute the image, repository contents or screenshots without permission.

## Why Juke-Nuke

Juke-Nuke is designed as one touchscreen-friendly entertainment system rather than a collection of separate interfaces. Karaoke is a major focus, with music, video, retro gaming and other shared-room entertainment alongside it.

## Quickest TrueNAS install

### 1. Create the persistent folders

```bash
sudo mkdir -p /mnt/APP_POOL/Juke-Nuke/{data,config,cache,uploads,backups,logs} && \
sudo chmod -R 770 /mnt/APP_POOL/Juke-Nuke
```

If your pool is not named `APP_POOL`, replace that part of the path with your own pool/dataset path.

### 2. Sign Docker into the private GitHub Container Registry

Use a GitHub token that can read the private package:

```bash
echo YOUR_GITHUB_TOKEN | sudo docker login ghcr.io -u YOUR_GITHUB_USERNAME --password-stdin
```

### 3. Clone this beta repo

```bash
git clone https://github.com/christianrobertson36/Juke-Nuke-Beta.git
cd Juke-Nuke-Beta
```

### 4. Check the media path

The supplied TrueNAS compose file expects your media library at:

```text
/mnt/tank/media
```

Edit `docker-compose.truenas.yml` if your library is elsewhere.

### 5. Start Juke-Nuke

```bash
sudo docker compose -f docker-compose.truenas.yml pull
sudo docker compose -f docker-compose.truenas.yml up -d
```

### 6. Open it

```text
http://YOUR-TRUENAS-IP:3105
```

### 7. Verify health

```bash
curl -fsS http://127.0.0.1:3105/health
```

Expected response includes:

```json
{"ok":true}
```

## Updating the beta

```bash
git pull
sudo docker compose -f docker-compose.truenas.yml pull
sudo docker compose -f docker-compose.truenas.yml up -d
```

## Logs

```bash
sudo docker compose -f docker-compose.truenas.yml ps
sudo docker compose -f docker-compose.truenas.yml logs --tail=200 juke-nuke
```

## Standard Docker / Dockge

For a normal Docker host or Dockge, use `docker-compose.yml` instead. It keeps its persistent data under a local `storage` directory and allows the port/media path to be overridden with environment variables.

## Beta reporting

The built-in **REPORT** button sends beta feedback directly back to the developer mailbox. Reviewers do not need to configure SMTP.

Please also check [KNOWN-ISSUES.md](KNOWN-ISSUES.md) before reporting a problem.

## Suggested areas to try

- First-run experience and media scanning
- Karaoke workflow
- Music playback and controls
- Movie/video playback and resume
- Metadata and artwork
- Retro/arcade features
- IPTV, if you use it
- Navigation/touchscreen usability
- Mobile/remote interaction
- Performance and stability

## Current beta image

```text
ghcr.io/christianrobertson36/juke-nuke:v1
```

The image is private and fixed to `v1` for this review period.
