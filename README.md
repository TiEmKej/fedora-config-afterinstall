# Step 1 - Update repo
```
sudo dng upgrade
```
# Step 2 - Fix the audio
```
sudo dnf install alsa-tools -y
wget https://github.com/joshuagrisham/galaxy-book2-pro-linux/raw/main/sound/necessary-verbs.sh
chmod +x necessary-verbs.sh
sudo ./necessary-verbs.sh
```
# Step 3 - Create a service file for `necessary-verbs.sh`
```
sudo nano /etc/systemd/system/necessary-verbs.service
```
File content
