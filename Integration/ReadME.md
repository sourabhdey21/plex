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

To ensure that the NFS share is mounted automatically on system boot, you can add an entry to the `/etc/fstab` file. Open the file in a text editor and add the following line:

```bash
plex_server_ip:/mnt/nfs_share /opt/plexmedia nfs defaults 0 0
```

Replace `plex_server_ip` with the IP address of the NFS server. Save the file and exit the text editor.


