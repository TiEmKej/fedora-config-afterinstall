# Setting things up on LG Gram 16 2023
My own repo with things I have to do after fresh install to start working with my Fedora installation on my LG Gram Laptop
## Must do after install
### Step 1 - Update packages
```
sudo dng upgrade
```
### Step 2 - Enable flatpak
```
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
### Step 3 - Fix the audio
Download alsa-tools package and fix script
```
sudo dnf install alsa-tools -y
wget https://github.com/joshuagrisham/galaxy-book2-pro-linux/raw/main/sound/necessary-verbs.sh
```
Add execute permision on file
```
chmod +x necessary-verbs.sh
```
Create folders for scripts and move the `necessary-verbs.sh`
```
sudo mkdir /usr/startup-scripts
sudo mv ~/necessary-verbs.sh /usr/startup-scripts/necessary-verbs.sh
```
Create a service file for `necessary-verbs.sh`
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
## Apps and other things
List of apps I often use on my system
### Programming
VSCodium
```
flatpak install flathub com.vscodium.codium
```
.NET 8.0 SDK
```
sudo dnf install dotnet-sdk-8.0
```
### Social
Vesktop (Discord fork)
```
flatpak install flathub dev.vencord.Vesktop
```
Signal messenger
```
flatpak install flathub org.signal.Signal
```
### Tools and office
Brave Browser
```
flatpak install flathub com.brave.Browser
```
Thunderbird
```
flatpak install flathub org.mozilla.Thunderbird
```

### Customization
Extension Manager for GNOME
```
flatpak install flathub com.mattjakeman.ExtensionManager
```
