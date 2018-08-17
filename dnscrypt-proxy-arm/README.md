# dnscrypt-proxy-arm

dnscrypt-proxy 2 on an ARM base image

## usage

```
docker create \
--name=plex \
--net=host \
-e VERSION=latest \
-e PUID=<UID> -e PGID=<GID> \
-e TZ=<timezone> \
-v </path/to/library>:/config \
-v <path/to/tvseries>:/data/tvshows \
-v </path/to/movies>:/data/movies \
-v </path for transcoding>:/transcode \
linuxserver/plex
```

## parameters

- `--net=host - Shares host networking with container, required.`
- `-v /config - Plex library location. This can grow very large, 50gb+ is likely for a large collection.`
- `-v /data/xyz - Media goes here. Add as many as needed e.g. /data/movies, /data/tv, etc.`
- `-v /transcode - Path for transcoding folder, optional.`
- `-e VERSION=latest - Set whether to update plex or not - see Setting up application section.`
- `-e PGID= for for GroupID - see below for explanation`
- `-e PUID= for for UserID - see below for explanation`
- `-e TZ - for timezone information eg Europe/London, etc`
