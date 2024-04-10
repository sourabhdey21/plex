## Step 1: Configuring Plex Media Server on Plex Server 

Before starting the Plex setup wizard, you can first create the directories that will store the Plex media files:

```bash
sudo mkdir -p /opt/plexmedia/{movies,series}
```

The Plex Media Server runs as the user plex, which must have read and execute permissions to the media files and directories. To set the correct ownership, enter the following command:

```bash
sudo chown -R plex: /opt/plexmedia
```
## Step 2: Mounting NFS Share

```bash
sudo mount -t nfs plex_server_ip:/mnt/nfs_share /opt/plexmedia
```

Replace `plex_server_ip` with the IP address of the NFS server.
