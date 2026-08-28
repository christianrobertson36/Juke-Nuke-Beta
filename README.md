# Juke-Nuke Beta

## The self-hosted digital jukebox for your man cave, games room or home bar

Juke-Nuke is a room-first entertainment system built for the places where people actually gather: a man cave, games room, home bar, garage, party room or big-screen lounge.

It started as a modern self-hosted **jukebox**, then grew all the trimmings around it: music, karaoke, movies, video, photos, radio, IPTV, retro gaming, playlists, touchscreen control, Xbox controller support, remote interaction and shared playback — all in one interface.

Instead of jumping between separate apps for music, karaoke, video and retro gaming, Juke-Nuke is designed to be left running on the screen in the room and used like part of the room itself.

> **Beta build:** Juke-Nuke is still pre-release software. This repo contains the public beta installer, documentation and feedback information. The main development source remains separate.

## What makes Juke-Nuke different

Juke-Nuke is not trying to be another generic media server.

The idea is closer to a **digital jukebox / entertainment console**:

- walk up to a touchscreen and pick music
- hand someone an Xbox controller and jump into retro gaming
- switch to karaoke when people want to sing
- put a movie or video on the big screen
- use radio or IPTV without leaving the interface
- build playlists for the night
- control playback from another device
- keep one consistent interface for the whole room

That is the point of the all-in-one design: not replacing four servers just for the sake of it, but giving a dedicated entertainment room one system that ties everything together.

## Main features

### Jukebox & music

- Music library and playback
- Album artwork and metadata
- Playlists
- Shared playback state
- Touchscreen-friendly controls
- Remote / companion control
- Persistent player controls across the interface

### Karaoke

- Dedicated karaoke area
- Singer workflow
- Queue-style use for shared rooms and parties
- Designed for a big-screen / social environment rather than just personal playback

Karaoke is one of the areas Juke-Nuke is particularly focused on during the beta because there are relatively few polished self-hosted options aimed at a home entertainment-room setup.

### Retro & arcade

- Retro / arcade section
- Emulator-focused workflow
- Xbox controller support for couch or games-room use
- Designed to sit alongside the jukebox rather than requiring a separate frontend

ROM and BIOS compatibility varies by system and remains an active beta area.

### Movies & video

- Movie and video libraries
- Resume behaviour for supported playback
- Playback controls integrated with the wider Juke-Nuke interface
- TMDB metadata and artwork enrichment
- Local sidecar artwork support

### More built in

- Photos
- Internet / local radio
- IPTV
- Playlists
- Shared playback state
- Mobile / remote interaction
- Touchscreen navigation
- TV / big-screen friendly interface
- Docker / TrueNAS deployment
- Windows and Android application work underway

## Built for a room, not just a browser tab

Juke-Nuke makes the most sense when it is treated like an appliance in the room:

- wall-mounted touchscreen
- countertop jukebox screen
- TV or projector
- home-bar display
- games-room monitor
- arcade-style cabinet
- couch setup with an Xbox controller

The goal is that guests do not need to know which server handles which type of media. They just use Juke-Nuke.

## Quickest TrueNAS install

### 1. Create the persistent folders

```bash
sudo mkdir -p /mnt/APP_POOL/Juke-Nuke/{data,config,cache,uploads,backups,logs} && \
sudo chmod -R 770 /mnt/APP_POOL/Juke-Nuke
```

If your pool is not named `APP_POOL`, replace that part of the path with your own pool/dataset path.

### 2. Clone the beta repo

```bash
git clone https://github.com/christianrobertson36/Juke-Nuke-Beta.git
cd Juke-Nuke-Beta
```

### 3. Check the media path

The supplied TrueNAS compose file expects your media library at:

```text
/mnt/tank/media
```

Edit `docker-compose.truenas.yml` if your library is elsewhere.

### 4. Start Juke-Nuke

```bash
sudo docker compose -f docker-compose.truenas.yml pull
sudo docker compose -f docker-compose.truenas.yml up -d
```

### 5. Open it

```text
http://YOUR-TRUENAS-IP:3105
```

### 6. Verify health

```bash
curl -fsS http://127.0.0.1:3105/health
```

Expected response includes:

```json
{"ok":true}
```

## Standard Docker / Dockge

For a normal Docker host or Dockge, use `docker-compose.yml` instead. Persistent data is kept under a local `storage` directory and the port/media path can be changed with environment variables.

See [INSTALL.md](INSTALL.md) for the fuller installation notes.

## Updating the beta

```bash
git pull
sudo docker compose -f docker-compose.truenas.yml pull
sudo docker compose -f docker-compose.truenas.yml up -d
```

## Beta reporting

Juke-Nuke includes a built-in **REPORT** button that sends beta feedback directly back to the developer mailbox, so testers do not need to configure an email client.

Also see:

- [FEATURES.md](FEATURES.md)
- [KNOWN-ISSUES.md](KNOWN-ISSUES.md)
- [FEEDBACK.md](FEEDBACK.md)
- [CHANGELOG.md](CHANGELOG.md)

## Good things to try

- Use it as a music jukebox for an evening
- Try it from a touchscreen or TV
- Navigate with an Xbox controller where supported
- Run a karaoke session
- Test the retro / arcade section
- Play movies and resume them later
- Try IPTV or radio
- Use the remote / companion features
- Leave it running as the main interface for a games room or home bar

The most useful feedback is not whether every individual feature can beat a dedicated specialist app. It is whether the whole thing works as a **single entertainment system for the room**.

## Current beta image

```text
ghcr.io/christianrobertson36/juke-nuke:v1
```

Juke-Nuke is under active development. Expect rough edges, report what breaks, and help shape what the finished jukebox becomes.
