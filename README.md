# Docker-Compose Seedbox Build #

## Assumptions ##
  - `docker` and `docker-compose` are installed on the host
  - file server storage is accessed via `/mnt/plex` on the host
  - `/downloads` and `/opt/homepage` are writable folders

## Containers used by Seedbox ##
  - Portainer
  - Homepage
  - Medusa
  - Radarr
  - Flood
  - Transmission
  - Jackett
  - NZBGet

## Initial Setup ##
Initial docker-compose file was generated with [docker-autocompose](https://github.com/Red5d/docker-autocompose), using the following command:

`docker run --rm -v /var/run/docker.sock:/var/run/docker.sock ghcr.io/red5d/docker-autocompose Medusa Flood NZBGet Radarr Transmission Jackett