# Opensuse-Ad-Join-Script

**Should work on OpenSUSE Leap 15.3, 15.2 older versions are untested)**

## How to use

### 1. Download script

```
git clone https://github.com/marekbeckmann/Opensuse-Ad-Join-Script.git ~/join-ad
cd ~/join-ad && chmod +x join-ad.sh
```
### 2. Run the script

```
sudo ./join-ad.sh
```

You can run the script with the following parameters: 


| Option | Description |
|--|--|
| `-h` `--help` | Prints help message, that shows all options and a short description |
| `-d` `--ad-domain` `<domain>` | Specifies domain to join |
| `-u` `--admin-user` `<userName>` | Specifies privileged user for AD join |
| `-p` `--homedir` `<directory>` | Overrides home directory for SSSD config (Defaults to `/home/%u@%d`) |
| `-s` `--shell` `<shell>`| Overrides shell for SSSD config |
| `-m` `--umask` `<umask>` | Specify UMASK for the homedir of users |
| `-a` `--allow-user` `<user1,user2>` | Allow user(s) (comma seperated) |
| `-r` `--allow-group` `<group1,group2>` | Allow group(s) (comma seperated) |
| `-e` `--enable-sudo` `<user1,user2>` | Allow user(s) to have root privileges (SUDO) |


**Example:**
```
bash join-ad.sh --adminuser Admin --ad-domain ad.example.org --homedir /home/%d/%u --shell /bin/bash --umask 0077 --allow-group Admins --enable-sudo Admin
```
This will join the ad (realm ad.example.org), using the privileged user `Admin`and setting the home directory for new users to `/home/ad.example.org/userName` and overriding the shell for every user to `/bin/bash` aswell as granting the user `Admin`  sudo privileges.