# plasma-bigscreen-minimal-fedora

https://fedoraproject.org/misc/#everything

<img width="1402" height="368" alt="Screenshot_20261024_214147" src="https://github.com/user-attachments/assets/3e56114d-1e40-491c-abf6-2dd490c7533e" />

```sh
sudo dnf install plasma-bigscreen plasma-nm kde-connect dolphin plasma-systemmonitor
```
```sh
printf '[Wallet]\nEnabled=false' > ~/.config/kwalletrc
```
```sh
sudo firewall-cmd --add-service=kdeconnect --permanent
```
```sh
sudo firewall-cmd --reload
```
```sh
sudo usermod -aG input $USER
```
```sh
sudo dnf install cool-retro-term fastfetch
```
```sh
sudo dnf install plasma-login-manager
```
```sh
sudo systemctl enable --force plasmalogin.service
```
```sh
sudo systemctl set-default graphical.target
```
```sh
sudo systemctl start plasmalogin.service
```
<img width="1039" height="631" alt="Screenshot_20261024_233523" src="https://github.com/user-attachments/assets/ecaa11db-3134-4213-bf32-8ece945edd3d" />
<img width="1039" height="631" alt="Screenshot_20261024_234559" src="https://github.com/user-attachments/assets/6973b83d-0844-4447-adbd-d84ac593bb9b" />
<img width="1172" height="752" alt="Screenshot_20261025_012817" src="https://github.com/user-attachments/assets/81ad0333-2952-4794-99da-a7266c250b9d" />

```sh
sudo dnf install flatpak
```
```sh
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

log in and out, or else we wont see flatpaks

```sh
flatpak install io.github.kolunmi.Bazaar it.mijorus.gearlever
```

Gear Lever hangs when trying to change destination for some reason.  
Other applications probably do the same.  
You want to setup some soft of soft reset keybind.
I'm using `META+CTRL+ALT+SHIFT+Backspace` to run:
```sh
systemctl --user exit
```
or, but more agressive:
```sh
sh -c "loginctl terminate-user $USER"
```

<img width="1091" height="426" alt="image" src="https://github.com/user-attachments/assets/e7951754-9deb-4f58-a0a7-8dfbb9867e75" />

you probably want to enable auto security updates
```sh
sudo dnf install dnf5-plugin-automatic
```
```sh
printf '%s\n' \
'[commands]' \
'apply_updates = yes' \
'download_updates = yes' \
'network_online_timeout = 60' \
'random_sleep = 0' \
'upgrade_type = security' \
'reboot = never' \
| sudo tee /etc/dnf/automatic.conf
```
```sh
sudo systemctl enable --now dnf5-automatic.timer
```
# Changing controller mapping
Plasma Bigscreen uses SDL  
I use AntiMicroX to configure bindings:
```sh
flatpak install io.github.antimicrox.antimicrox
```
Then save them to `~/.config/sdl-gamecontrollerdb.txt`, example:
```txt
030002afc82d000006310000140100001172012550,8BitDo Ultimate Wireless Controller,platform:Linux,a:b1,b:b0,x:b3,y:b2,back:b6,start:b7,guide:b8,leftshoulder:b4,rightshoulder:b5,leftstick:b9,rightstick:b10,leftx:a0,lefty:a1,rightx:a3,righty:a4,lefttrigger:a2,righttrigger:a5,dpup:h0.1,dpleft:h0.8,dpdown:h0.4,dpright:h0.2,
0500d6405e040000e0020000030900001118736,Xbox One Controller,platform:Linux,a:b1,b:b0,x:b3,y:b2,back:b6,start:b7,guide:b10,leftshoulder:b4,rightshoulder:b5,leftstick:b8,rightstick:b9,leftx:a0,lefty:a1,rightx:a3,righty:a4,lefttrigger:a2,righttrigger:a5,dpup:h0.1,dpleft:h0.8,dpdown:h0.4,dpright:h0.2,
```
To make them work on login:
```sh
printf "SDL_GAMECONTROLLERCONFIG_FILE=$HOME/.config/sdl-gamecontrollerdb.txt" > ~/.config/environment.d/60-sdl.conf
```
