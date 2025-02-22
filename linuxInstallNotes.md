# Linux install notes
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
  git octave
```
