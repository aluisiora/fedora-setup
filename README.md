# Fedora Setup
My Personal Fedora Setup

## System Font

| Type                  | Font                  |  Size |
|-----------------------|-----------------------|-------|
| Interface Text        | Lato Regular          |  10   |
| Document Text         | Lato Regular          |  10   |
| Monospace Text        | Cascadia Mono Regular |  10   |
| Legacy Windows Titles | Lato Bold             |  10   |

**Hinting**: Slight
**Antialiasing**: Subpixel

### Instalation

Lato:
```
sudo dnf install lato-fonts
```

Cascadia Code: [https://github.com/microsoft/cascadia-code](https://github.com/microsoft/cascadia-code)

Fira Code: [https://github.com/tonsky/FiraCode](https://github.com/tonsky/FiraCode)

### Better Fonts

Install copr:
```
sudo dnf copr enable dawid/better_fonts
sudo dnf install fontconfig-enhanced-defaults fontconfig-font-replacements
```

## Usefull Software

Install:
```
sudo dnf install vim gnome-tweaks tilix keepassxc @development-tools p7zip
```

### VSCode

```
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
sudo dnf check-update
sudo dnf install code
```

### Flathub

```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

#### Apps

Postman:
```
flatpak install flathub com.getpostman.Postman
```

Slack:
```
flatpak install flathub com.slack.Slack
```

Spotify:
```
flatpak install flathub com.spotify.Client
```

DBeaver:
```
flatpak install flathub io.dbeaver.DBeaverCommunity
```

### Docker

```
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
sudo dnf install docker-ce docker-ce-cli containerd.io
sudo usermod -aG docker $USER
sudo systemctl enable docker
sudo systemctl start docker
```

#### Switch to cgroups v1

Edit `/etc/default/grub` and add `systemd.unified_cgroup_hierarchy=0` to `GRUB_CMDLINE_LINUX`.

Generate new `grub.cfg`:
```
sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
```

## Generate SSH Key

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

## Gnome Extensions

- Always zoom workspaces
- Kstatusnotifieritem/appindicator support
- No topleft hot corner
- User themes