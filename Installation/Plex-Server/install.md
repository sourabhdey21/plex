## Step 1: Update and Upgrade System

```bash
sudo apt update
sudo apt upgrade
```

## Step 2: Add Plex Repository

```bash
echo deb https://downloads.plex.tv/repo/deb public main | sudo tee /etc/apt/sources.list.d/plexmediaserver.list
curl https://downloads.plex.tv/plex-keys/PlexSign.key | sudo apt-key add -
```

## Step 3: Install Plex Media Server

```bash
sudo apt update
sudo apt install plexmediaserver
```

## Step 4: Start and Enable Plex Media Server

```bash
sudo systemctl start plexmediaserver
sudo systemctl enable plexmediaserver
```

## Step 5: Check Plex Media Server Status

```bash
sudo systemctl status plexmediaserver
```

## Step 6: Adjust the Firewall

```bash
sudo ufw allow 32400/tcp
sudo ufw reload
```

## Step 7: Create UFW Application Profile

```bash
sudo nano /etc/ufw/applications.d/plexmediaserver
```

Copy the following into the file:

```bash
[plexmediaserver]
title=Plex Media Server (Standard)
description=The Plex Media Server
ports=32400/tcp|3005/tcp|5353/udp|8324/tcp|32410:32414/udp

[plexmediaserver-dlna]
title=Plex Media Server (DLNA)
description=The Plex Media Server (additional DLNA capability only)
ports=1900/udp|32469/tcp

[plexmediaserver-all]
title=Plex Media Server (Standard + DLNA)
description=The Plex Media Server (with additional DLNA capability)
ports=32400/tcp|3005/tcp|5353/udp|8324/tcp|32410:32414/udp|1900/udp|32469/tcp
```

Save the file and update profiles list:

```bash
sudo ufw app update plexmediaserver
```

Apply the new firewall rules:

```bash
sudo ufw allow plexmediaserver-all
```

Finally, check if the new firewall rules are applied successfully with:

```bash
sudo ufw status verbose
```


## Step 5: Configure Plex Media Server

Open a web browser and navigate to `http://localhost:32400/web` to complete the setup.
