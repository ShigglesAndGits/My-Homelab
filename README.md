# My-Homelab
This is a placeholder, most of my config information can be found at https://bironfamily.net/.
So this is an actually useful placeholder, here's the copy-and-pasted comments from docker-config.yml: 
  The following items will need to be configured prior to running this file: 
   - Install Docker, Docker Compose, and Portainer: https://www.linuxtuto.com/how-to-install-portainer-on-ubuntu-22-04/
   - Create your docker directory. I personally use /etc/docker-configs. You can use the mkdir command for this.
   - Set up network storage of some sort, whether it's an external hard drive plugged into a windows computer or (my recommendation) TrueNAS with mirrored 
     drive pools. Truenas is a project unto itself, but if you're interested, https://www.truenas.com/docs/core/gettingstarted/
   - Mount your NAS fileshares. Directions for Ubuntu: https://support.zadarastorage.com/hc/en-us/articles/213024986-How-to-Mount-a-SMB-Share-in-Ubuntu 
     Only one is necessary for media storage, if you only have one network share you can remove the additional volumes from each container. 
   - Add your dockerDir and nasDir0 (plus additional NAS directories if needed) to the accompanying .env file
   - Your NAS fileshares should be set up with the following subdirectories: 
    - movies
    - movieDownload
    - tv
    - tvDownload
    - defaultDownload
 
  Note: This is Linux, so all file paths and basically everything else is case sensitive. 
  Once this is running without error, refer to https://trash-guides.info/ for best practices and setup instructions for setting up each of the containers. 
 
  Docker basics: Everything on the left of a colon (:) is the value on your host, everything on the right is the value on the container. 
  Which means a line saying /etc/docker-configs:/var/lib says that your server's folder "docker-configs" located in your "etc" directory can be accessed 
  inside of the container by navigating to /var/lib.
  The same applies with ports. So if my server's IP is 192.168.0.100, and I wanted to access Sonarr, look at the list for Sonarr's ports. 
  I see that the left side of the colon for Sonarr's exposed ports is 8989, so to access Sonarr in a web browser I'd navigate to http://192.168.0.100:8989/.
 
  Inside this file, there are (currently) six containers: Jellyfin, JellySeerr, Sonarr, Radarr, Prowlarr, and Bazarr. 
  Jellyfin will serve your media (think yarr-harr netflix)
  Jellyseerr will add a nice friendly UI so your fiance can just log in and select a movie to queue the download, instead of harassing you for it. 
  Sonarr/Radarr will handle organizing your media and queuing downloads
  Prowlarr will manage your indexers, like IPTorrents, NZBGeek, etc
  Bazarr scans your library and auto-downloads subtitles. 
 
  These can be accessed on the following ports (In a web browser this would be http://[serverIP]:[port])
  Sonarr: 8989
  Radarr: 7878
  Jellyfin: 8096
  Jellyseerr: 5055
  Prowlarr: 9696
  Bazarr: 6767
