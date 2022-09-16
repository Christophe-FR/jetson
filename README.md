# jetson

## remote control
Follow https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit

```
sudo apt purge vino
sudo apt install vino
```

Create file "vnc_server.sh" with content:
```
export DISPLAY=:0
gsettings set org.gnome.Vino enabled true
gsettings set org.gnome.Vino prompt-enabled false
gsettings set org.gnome.Vino require-encryption false
/usr/lib/vino/vino-server &                            
```

Start the server with:
```
sh vnc_server.sh
```

Connect the jetson with VNC viewer (follow "Connecting to VNC service from another computer" on https://developer.nvidia.com/embedded/learn/tutorials/vnc-setup)

## Task scheduling
To run a bash script at startup
```
chmod +x startup.sh
sudo systemctl enable cron.service
sudo systemctl status cron.service
crontab -e
```
Add the following line at the end of the file:
```
@reboot /home/christophe/Desktop/startup.sh
```
