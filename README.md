# Setup for my Debian VM.

## Allow sudo
```
su root
```

```
sudo usermod -aG sudo user
```

## Set path to .local/bin
```
export PATH=$PATH:/home/user/.local/bin
```

## Installations
```
sudo apt install zsh stow neovim flatpak jq curl openvpn flameshot keepassxc iproute2 alacritty wget curl git lf syncthing
```

```
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

```
flatpak install flathub chat.simplex.simplex
```

```
sudo curl -fsSLo /usr/share/keyrings/mullvad-keyring.asc https://repository.mullvad.net/deb/mullvad-keyring.asc
```

```
echo "deb [signed-by=/usr/share/keyrings/mullvad-keyring.asc arch=$( dpkg --print-architecture )] https://repository.mullvad.net/deb/stable stable main" | sudo tee /etc/apt/sources.list.d/mullvad.list
```

```
sudo apt update
```

```
sudo apt install mullvad-browser
```

```
sudo apt-get update && sudo apt-get install -y gpg ca-certificates
sudo mkdir -p /etc/apt/keyrings
sudo gpg --keyserver hkps://keys.openpgp.org \
    --no-default-keyring --no-permission-warning --homedir $(mktemp -d) \
    --keyring gnupg-ring:/etc/apt/keyrings/fpf-apt-tools-archive-keyring.gpg \
    --recv-keys DE28AB241FA48260FAC9B8BAA7C9B38522604281
sudo chmod +r /etc/apt/keyrings/fpf-apt-tools-archive-keyring.gpg
```

```
. /etc/os-release
echo "deb [signed-by=/etc/apt/keyrings/fpf-apt-tools-archive-keyring.gpg] \
    https://packages.freedom.press/apt-tools-prod ${VERSION_CODENAME?} main" \
    | sudo tee /etc/apt/sources.list.d/fpf-apt-tools.list
```

```
sudo apt update
```

```
sudo apt install -y dangerzone
```

## VPN
```
git clone https://github.com/BarbossHack/RiseupVPN-OpenVPN.git
```

```
cd RiseupVPN-OpenVPN
```

```
./generate.sh
```

```
sudo openvpn --config riseup-ovpn.conf
```

```
curl ipinfo.io
```

## Configuration
```
git clone https://github.com/sekigetsu/debian-dotfiles.git
```

```
cd debian-dotfiles
```

```
stow.
```

## Final steps

```
sudo apt purge firefox-esr vim
```

```
chsh
```

```
rmdir Music Templates Public Videos
```

```
mkdir unsafe-pdfs cleaned-pdfs
```
