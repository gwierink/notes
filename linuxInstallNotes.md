# Linux install notes

## Debian 13
Update the system
```bash
sudo apt update && sudo apt upgrade
```

### Security
**Clamav  antivirus**
Test whether clamav exists
```bash
clamscan --version
freshclam --version
```

If these commands are missing, install the applications:
```bash
sudo apt install clamav clamav-daemon clamav-freshclam
```

**Using clamav**
Check the status
```bash
systemctl status clamav-freshclam
```

Inspect the database by
```bash
sudo freshclam
```

Enable automatic updates
```bash
sudo systemctl enable --now clamav-freshclam
```

Check the results
```bash
systemctl is-enabled clamav-freshclam
systemctl is-active clamav-freshclam
```bash

Start clamav
```bash
sudo systemctl enble --now clamav-daemon
```

Check status
```bash
systemctl status clamav-daemon --no-pager
```

**ufw firewall**
Check whether installed and active
```bash
sudo ufw status verbose
```

### Bit torrent
uBittorrent is good, but Transmission is lighter
```bash
sudo apt install -y transmission-daemon transmission-cli
```

### Printer-scanner
For a standard 64 bit system (tested on Debian 13),
[this guide](https://blog.oldo.org/2025/08/13/install-epson-scan-2-on-debian/)
worked.

The guide explains:
* Go to http://support.epson.net/linux/en/epsonscan2.php
* Click “Download” button for “deb” distribution type, “64bit(x86_64)” architecture
* Download of file like “epsonscan2-bundle-6.7.80.0.x86_64.deb.tar.gz” should start

Once the file is fully downloaded:
```bash
tar xvzf epsonscan2-bundle-6.7.80.0.x86_64.deb.tar.gz
cd epsonscan2-bundle-6.7.80.0.x86_64.deb
sudo ./install.sh
```

Now, the application should work from the graphics applications, or from the
terminal as:
```bash
epsonscan2
```

If "libQt5Widgets.so.5" is missing, install it:
```bash
sudo apt install libqt5widgets5
```


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
