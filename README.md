# Docker-Compose Seedbox Build #

## Assumptions ##
  - `docker` and `docker-compose` are installed on the host
  - file server storage is accessed via `/mnt/plex` on the host
  - `/downloads` and `/opt/homepage` are writable folders

## Containers used by Seedbox ##
  - Portainer (port 9443)
  - Homepage (port 4321)
  - Medusa (port 8081)
  - Radarr (port 7878)
  - Flood (port 3000)
  - Transmission (port 9091)
  - Jackett (port 9117)
  - NZBGet (port 6789)

## Initial Setup ##
  - Update all occurances of `x.x.x.x` with the host's IP address
  - Change server storage mount to suit your environment by changing all occurances of `/mnt/plex` to match
  - Change downloads folder to suit your environment by changing all occurances of `/downloads` to match

## Install ##
  - Clone this repo to your host machine with the following command:
    - `git clone https://github.com/ksolomon/Seedbox-Docker-Compose-Build.git`
  - Change to the new folder and run the following command:
    - `docker-compose -f seedbox-stack.yaml up -d`

## Homepage Setup ##
  - Edit the `/opt/homepage/docker.yaml` file and remove the comments from the socket lines at the bottom of the file.  The interface will refresh automatically, showing the services that were installed by the compose script.
  - Other files in `/opt/homepage` can be edited to add other services/sites.

## Notes ##
Initial docker-compose file was generated with [docker-autocompose](https://github.com/Red5d/docker-autocompose), using the following command:

`docker run --rm -v /var/run/docker.sock:/var/run/docker.sock ghcr.io/red5d/docker-autocompose Medusa Flood NZBGet Radarr Transmission Jackett homepage portainer > seedbox-stack.yaml`
