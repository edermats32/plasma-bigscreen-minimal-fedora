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
