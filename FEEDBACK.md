# Juke-Nuke Beta Feedback

Thanks for trying the beta.

## Fastest way to report something

Use the built-in **Report** button inside Juke-Nuke. The beta image is already configured to send reports back to the developer mailbox, so reviewers do not need to configure SMTP.

## What to include

Useful bug reports contain:

- Juke-Nuke version
- TrueNAS / Docker version
- Browser or device
- Media type being tested
- Steps to reproduce
- Expected result
- Actual result
- Screenshot or relevant logs where useful

## Logs

Standard Docker:

```bash
docker compose logs --tail=200 juke-nuke
```

TrueNAS compose:

```bash
docker compose -f docker-compose.truenas.yml logs --tail=200 juke-nuke
```

## Especially useful beta feedback

- First-run setup
- TrueNAS / Docker installation
- Navigation and touchscreen usability
- Karaoke workflow
- Music playback
- Movie/video playback and resume
- Metadata and artwork
- Retro / arcade compatibility
- IPTV behaviour
- Mobile / remote interaction
- Performance and stability

Please check `KNOWN-ISSUES.md` before reporting something already listed.
