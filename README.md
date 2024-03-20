# Setting things up on LG Gram 16 2023
## Step 1 - Update repo
```
sudo dng upgrade
```
## Step 2 - Enable flatpak
```
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
## Step 3 - Fix the audio
```
sudo dnf install alsa-tools -y
wget https://github.com/joshuagrisham/galaxy-book2-pro-linux/raw/main/sound/necessary-verbs.sh
chmod +x necessary-verbs.sh
```
## Step 4 - Create folders for scripts and move the `necessary-verbs.sh`
```
sudo mkdir /usr/startup-scripts
sudo mv ~/necessary-verbs.sh /usr/startup-scripts/necessary-verbs.sh
```
## Step 5 - Create a service file for `necessary-verbs.sh`
```
sudo nano /etc/systemd/system/necessary-verbs.service
```
File content
```
[Unit]
Description=Audio fix

[Service]
Type=simple
ExecStart=/bin/bash /usr/startup-scripts/necessary-verbs.sh

[Install]
WantedBy=multi-user.target
```
Start the script and turn on autorun
```
sudo systemctl start necessary-verbs.service
```
