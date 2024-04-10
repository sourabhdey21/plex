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
/mnt/nfs_share client_ip(rw,sync,no_subtree_check)
```

Replace `client_ip` with the IP address of the client that will be accessing the NFS share.

## Step 4: Start the NFS Server

```bash
sudo systemctl start nfs-kernel-server
sudo systemctl enable nfs-kernel-server
```

## Step 5: Install NFS Client on the Client Machine

```bash
sudo apt update
sudo apt install nfs-common
```

## Step 6: Mount the NFS Share on the Client Machine

```bash
sudo mount -t nfs server_ip:/mnt/nfs_share /mnt/local_mount_point
```

Replace `server_ip` with the IP address of the NFS server and `/mnt/local_mount_point` with the local directory where you want to mount the NFS share.

## Step 7: Verify the NFS Share

```bash
df -h
```

You should see the NFS share listed in the output.

## Step 8: Unmount the NFS Share

```bash
sudo umount /mnt/local_mount_point
```

This will unmount the NFS share from the client machine.

