# Intro

This deploys all the STARR services on a shared docker bridge. I've also added overseer which allows a single place to browse and request content, all authenticated through plex or local accounts.

# Services Deployed

- [flaresolverr](https://github.com/FlareSolverr/FlareSolverr)
- [prowlarr](https://github.com/Prowlarr/Prowlarr)
- [radarr](https://github.com/Radarr/Radarr)
- [sonarr](https://github.com/Sonarr/Sonarr)
- [qBittorrent](https://github.com/qbittorrent/qBittorrent)
- [overseerr](https://github.com/sct/overseerr)
- [plex](https://www.plex.tv/)

# File Structure

The template uses the below file structure, with hard links, to organize content. This allows the user of local storage or a Network File System (NFS) share.

The benefit of using hard links, unlike a soft link, is if the original file is deleted, the data still exists under the secondary hard link. This allows files to live in both downloads and media without taking up any additional space. It also means we can allow our download client, qBittorrent, to delete the file in the downloads directory without it affecting the link in the media file.

```
data
├── downloads
└── media
     ├── movies
     └── tv
```

## Steps that are yet to be automated

We need to give the `data` directory the correct permissions on the Docker host machine.

```bash
sudo chown -R $USER:$USER /data
sudo chmod -R a=,a+rX,u+w,g+w /data
```
