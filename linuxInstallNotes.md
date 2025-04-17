# Linux install notes

## Debian 12
### Basic packages
```bash
sudo apt install \
    gedit vim ufw git octave \
    python3-numpy python3-matplotlib
```
### Obsidian
Download the deb package from https://obsidian.md/download and set up a place
for your tools (if not done already):
```bash
mkdir ~/tools/obsidian && cd !$
mv ~/Downloads/obsidian_1.8.9_amd64.deb .
sudo dpkg -i obsidian*.deb
```
In case the system complains about missing dependencies, do
```bash
sudo apt --fix-broken install
```


## OpenSUSE-15.6 Leap
### Basic system setup
**Changing hostname**
1. Display the current hostname.
```bash
user@linux-ui1m:~> hostname
linux-ui1m
```

2. Change the hostname using the hostnamectl command to "host"
```bash
user@linux-ui1m:~> sudo hostnamectl set-hostname host
[sudo] password for root:
```

3. Verify the new hostname by displaying it again.
```bash
user@linux-ui1m:~> hostname
host
```bash

4. The shell prompt is not immediately updated as `$PS1` is only set when a new
   shell is started. Start a new shell session to reflect the updated hostname.
```bash
user@linux-ui1m:~> bash
user@host:~>
```bash

Source: https://www.simplified.guide/suse/change-hostname

**Audio problem**
```bash
rpm -q alsa alsa-utils alsa-firmware
sudo zypper in alsa-firmware
sudo systemctl restart alsasound
```
Source: https://en.opensuse.org/SDB:Audio_troubleshooting

### Packages
```bash
sudo zypper in \
  git octave rstudio \
  python3-numpy python3-matplotlib
```
