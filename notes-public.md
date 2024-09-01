
# macOS and Linux Command Cheat Sheet
# SCP
```bash
scp username@127.0.0.0:/path/to/file.ext /path/to/save/file.ext
```
# Checksums:
## SHA Checksum
```bash
shasum -a 256 /path/to/file
openssl sha256 /path/to/file
```


## MD5 Checksum
### macOS
```bash
md5 /path/to/file
```
**To check both:**
```bash
openssl sha256 /path/to/file; md5 /path/to/file
```

### Windows:
```powershell
certutil -hashfile Example.txt MD5
```
```powershell
Get-FileHash .\Downloads\KeePass-2.50-Setup.exe -Algorithm MD5
```

# Finding Python or other files
```bash
$Path | grep python
```

# Git
```bash
git config --global --unset-all user.name
git config --global --unset user.email
git config --global user.name "FIRST_NAME LAST_NAME"
git config --global user.email "MY_NAME@example.com"
```
## Git Basics
### Create New local Git Repository:
```zsh
git init
```
### Copy a repository
```zsh
git clone
```
### Add a file as it looks now to our next commit(stage):
```zsh
git add
```
### create a snapshot of the changes and save it to the git directory:
```zsh
git commit
```
### Push local changes to the original:
```zsh
git push
```

## Make a Change
#### List new or modified files not yet committed
```zsh
git status
```
### Lists down changes and conflicts
```zsh
git diff
```
### Stage file ready for commit:
```zsh
git add <file>
```
### Un-stage a file, keep the file changes
```zsh
git reset <file>
```
### Commit all staged files to versioned history:
```zsh
git commit -m 'Your Message Here'
```
## Git Branching & Merging:
#### List branches:
```zsh
git branch
```
### Switch to another branch and check it out into your working dir:
```zsh
git checkout
```
### Merge the specified branch's history into the current branch:
```zsh
git merge
```
### Show all commits in the current branch:
```zsh
git log
```
## Share and Update
### Create new remote repo connection:
```zsh
git remote add <name> <url>
```
### Get all changes from the origin (no merge):
```zsh
git fetch
```
### Get all latest changes from the origin and merge:
```zsh
git pull
```
### Upload your local repo changes to the origin remote repo:
```zsh
git push
```

Visit [https://support.atlassian.com/bitbucket-cloud/docs/configure-your-dvcs-username-for-commits/](https://support.atlassian.com/bitbucket-cloud/docs/configure-your-dvcs-username-for-commits/) for more information.

# GitHub
<!-- links can be just pasted or use the [text](url) format -->
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent<br>
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

Visit [https://docs.github.com/en/authentication/connecting-to-github-with-ssh](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) for more information.


# Changing default startup GUI or CLI

## Start GUI on Console:
```bash
  sudo systemctl start gdm
```
```bash
  sudo systemctl start graphical.target
```
## To set GUI default:
```bash  
  sudo systemctl set-default graphical.target
```
## To set to Console default:
```bash
  sudo systemctl set-default multi-user.target
```
## To check which is the default startup option:
```bash
  sudo systemctl get-default
```

# Converting man page from terminal to postscript (.ps) and then to a PDF
```bash
man -t hping3 > hping3.ps
```
## macOS conversion:
```bash
pstopdf hping3.ps
```
## Linux conversion:
```bash
ps2pdf hping3.ps
```

# Aliases on Debian
```bash
vi /etc/bashrc
```
```bash
add alias ll='ls -alh'
```
```bash
:wq
```
```bash
source /etc/bashrc
```
# Tarball and Gunzip:
## tar.gz extraction
```bash
tar -xvzf /path/to/file/to/extract.tar.gz
tar -xvzf path/to/file/to/extract.tar.gz -C /path/to/directory/to/save
```

## tar.gz creation
```bash
tar -cvzf FileNameForFile.tar.gz /path/to/dir/or/file/to/compress
```

## tar.gz list files
```markdown
tar -tvzf /path/to/file.tar.gz
```

# Change Button order on Mate ParrotOS

Use the `dconf` editor, which should be provided.<br>
`Applications` > `System Tools` > `dconf Editor`
Select `org` > `mate` > `marco` > `general` > `button-layout` > <br>
For Right side: `menu:` `minimize`, `maximize`, `close` <br>
For Left side: `minimize`, `maximize`, `close:menu`. You can also add spacer to separate any of the buttons.


# Less command
<!-- uses two spaces for new line or html tag <br> -->
`u` - up half page  
`d` - down half page<br>
`k` - scroll single line up
`j` - scroll single line down  
`-i` - case insensitive searching unless pattern contains capitals (as clo or in less)  
`/` - /pattern/ - search (used with n)  
`-p` /pattern/ open file at /pattern/ (as clo)  
`& /pattern/` show lines containing /pattern/ (like grep)  
<!-- below [Text](command/image file/or url) -->
[https://github.com/cavaunpeu/markdown-insert-screenshot/blob/master/README.md](https://github.com/cavaunpeu/markdown-insert-screenshot/blob/master/README.md) Appears to be a good link for taking screenshots for markdown files. 

# screen command serial connection
## macOS:
```zsh
screen <port_name> <baud rate>
```
To disconnect, type `control-a` followed by `control-\` The screen will then ask if you are sure you want to disconnect.  
Example:
```zsh
screen tty.usbserial 115200
```
close:
```zsh
control a
control \
```

## Linux:
```zsh
screen <port_name> <baud rate>
```
To disconnect, type `control-a` then `shift-k`.  
Example:
```zsh
screen tty.usbserial 115200
```
close:
```zsh
control a
shift k
```

# LVM (Logical Volume Manager)
## Creating Physical Volume
1. First validate that the system sees the disks you will be using to create your Volume Group with
`lsblk` in our example our disk is `sdb`
2. Now see if the disk is mounted and if it is, unmount the disk(s) with the following commands `mount | grep /dev/sdX` where `X` in our case would be b (`mount | grep /dev/sdb`) If the disk is mounted it should show with that command. You will need to unmount the disk with this command `umount /dev/sdX` where `X` in our case would be b (`umount /dev/sdb`)
3. Now create a physical volume using the `pvcreate` command. ```
```zsh
pvcreate /dev/sda
pvcreate /dev/sdb
```
4. Validate the Physical Volume was created by using `pvscan` and `pvdisplay` and `pvs`
## Creating and extending a Volume Group
1. Now create a new volume group with the `vgcreate` command. If using more then one physical drives you will need to extend the Volume Group using `vgextend`
```zsh
vgcreate vg-test /dev/sda
vgextend vg-test /dev/sdb
```
2. Now validate that the Volume Group was created. `vgscan` or `vgdisplay` or `vgs`

## Creating a Logical Volume
1. Now create 2 Logical Volumes following the previously stated 2/3 1/3 rule.
```zsh
lvcreate -l +66%FREE -n test0 vg-test && lvcreate -l +100%FREE -n test1 vg-test
```
2. Now validate the Logical Volume has been created properly with `lvs` and `lsblk`
## Applying a Filesystem and mount point
1. Format the Logical Volumes to use Ext4 Filesystem
```zsh
mkfs.ext4 /dev/vg-test/test0 && mkfs.ext4 /dev/vg-test/test1
```
2. Now create the Directories the new LVs will mount to. 
```zsh
mkdir /test0 && mkdir /test1
```
3. Add permanent mount points to the fstab file so the new LVs will mount to /dvr0,/dvr1 on boot. Add the following to /etc/fstab
```zsh
/dev/vg-test/test0 /test0 ext4 defaults 0 0
/dev/vg-test/test1 /test1 ext4 defaults 0 0
```
4. Run `mount -a` to verify the changes to the fstab file and run `lsblk` to verify that the LVs mounted. If the `mount -a` command is successful there will be no output. If there is a problem you will see the issue returned in the terminal
# Unattended Upgradess on Linux
## Debian:
Run the following as root:
1. ```bash
    apt update && apt upgrade -y
    ```
2. ```bash
    apt install unattended-upgrades
    ```
3. Edit the configuration file as needed from the defaults.
    ```bash
    vi /etc/apt/apt.conf.d/50unattended-upgrades
    ```
[source](https://wiki.debian.org/UnattendedUpgrades)