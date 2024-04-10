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

## Step 5: Configure Plex Media Server

Open a web browser and navigate to `http://localhost:32400/web` to complete the setup.
