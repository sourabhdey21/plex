## Step 1: Install NFS Server

```bash
sudo apt update
sudo apt install nfs-kernel-server
```

## Step 2: Create a Directory for NFS Shares

```bash
sudo mkdir -p /mnt/nfs_share
```

## Step 3: Configure NFS Exports

Edit the `/etc/exports` file and add the following lines:

```bash
/mnt/nfs_share plex_server_ip(rw,sync,no_subtree_check)
```

Replace `plex_server_ip` with the IP address of the Plex server that will be accessing the NFS share.

## Step 4: Start the NFS Server

```bash
sudo systemctl start nfs-kernel-server
sudo systemctl enable nfs-kernel-server
```

## Step 5: Check the Status of the NFS Server

```bash
sudo systemctl status nfs-kernel-server
```

🎉 Congratulations! You have successfully set up your NFS server. 🎉
