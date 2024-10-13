# File and Directory Permissions Overview

```
[root@localhost Rohail]# ls -l
total 8
-r--r--r--. 1 rohail rohail 66 Oct 12 03:59 file1
-rw-rw-r--. 1 rohail rohail 85 Oct 12 05:40 file2
-rw-rw-r--. 1 rohail rohail  0 Oct 12 07:13 file3
----------. 1 root   root    0 Oct 12 07:22 file4
drwxr-x---. 2 rohail rohail 42 Oct 13 12:19 folder1
drwxr-x---. 2 rohail rohail  6 Oct 13 12:18 folder2
drwxr-x---. 2 rohail rohail  6 Oct 13 12:18 folder3
```

```
[root@localhost Desktop]# cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
games:x:12:100:games:/usr/games:/sbin/nologin
ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin
nobody:x:99:99:Nobody:/:/sbin/nologin
systemd-network:x:192:192:systemd Network Management:/:/sbin/nologin
dbus:x:81:81:System message bus:/:/sbin/nologin
polkitd:x:999:998:User for polkitd:/:/sbin/nologin
libstoragemgmt:x:998:995:daemon account for libstoragemgmt:/var/run/lsm:/sbin/nologin
colord:x:997:994:User for colord:/var/lib/colord:/sbin/nologin
rpc:x:32:32:Rpcbind Daemon:/var/lib/rpcbind:/sbin/nologin
saned:x:996:993:SANE scanner daemon user:/usr/share/sane:/sbin/nologin
gluster:x:995:992:GlusterFS daemons:/run/gluster:/sbin/nologin
saslauth:x:994:76:Saslauthd user:/run/saslauthd:/sbin/nologin
abrt:x:173:173::/etc/abrt:/sbin/nologin
setroubleshoot:x:993:990::/var/lib/setroubleshoot:/sbin/nologin
rtkit:x:172:172:RealtimeKit:/proc:/sbin/nologin
pulse:x:171:171:PulseAudio System Daemon:/var/run/pulse:/sbin/nologin
radvd:x:75:75:radvd user:/:/sbin/nologin
chrony:x:992:987::/var/lib/chrony:/sbin/nologin
unbound:x:991:986:Unbound DNS resolver:/etc/unbound:/sbin/nologin
qemu:x:107:107:qemu user:/:/sbin/nologin
tss:x:59:59:Account used by the trousers package to sandbox the tcsd daemon:/dev/null:/sbin/nologin
sssd:x:990:984:User for sssd:/:/sbin/nologin
usbmuxd:x:113:113:usbmuxd user:/:/sbin/nologin
geoclue:x:989:983:User for geoclue:/var/lib/geoclue:/sbin/nologin
ntp:x:38:38::/etc/ntp:/sbin/nologin
gdm:x:42:42::/var/lib/gdm:/sbin/nologin
rpcuser:x:29:29:RPC Service User:/var/lib/nfs:/sbin/nologin
nfsnobody:x:65534:65534:Anonymous NFS User:/var/lib/nfs:/sbin/nologin
gnome-initial-setup:x:988:982::/run/gnome-initial-setup/:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
avahi:x:70:70:Avahi mDNS/DNS-SD Stack:/var/run/avahi-daemon:/sbin/nologin
postfix:x:89:89::/var/spool/postfix:/sbin/nologin
tcpdump:x:72:72::/:/sbin/nologin
rohail:x:1000:1000:Rohail Rathore:/home/rohail:/bin/bash
user1:x:1001:1001::/home/user1:/bin/bash
user2:x:1002:1002::/home/user2:/bin/bash
ruser1:x:1003:1003::/home/ruser1:/bin/bash
ruser2:x:1004:1004::/home/ruser2:/bin/bash
```
---
```
username:password:UID:GID:comment:home_directory:shell
```

## Explanation of Each Field:

1. **`username`**: The login name of the user (e.g., `root`, `rohail`, `bin`).
2. **`password`**: Historically, this field stored encrypted passwords, but modern systems store passwords in `/etc/shadow` for security. The `x` here indicates that the password is stored in `/etc/shadow`.
3. **`UID`**: The user ID, a unique number assigned to each user. For example, `root` has UID `0`.
4. **`GID`**: The group ID, representing the primary group the user belongs to. For example, `root` has GID `0`, and `rohail` has GID `1000`.
5. **`comment`**: This field often holds a description or comment about the user. For system users, it may describe their role (e.g., `FTP User`, `RealtimeKit`). For personal accounts, it may include the full name (e.g., `Rohail Rathore`).
6. **`home_directory`**: The path to the user's home directory. For example, the home directory for `root` is `/root`, while the home directory for `rohail` is `/home/rohail`.
7. **`shell`**: The login shell assigned to the user, which is the program that runs when the user logs in. Common shells include `/bin/bash` and `/sbin/nologin`. The latter (`/sbin/nologin`) is used to prevent login access for system users.

## Example Breakdown:
Let's break down a few examples:

### 1. `root:x:0:0:root:/root:/bin/bash`
- **Username**: `root`
- **Password**: `x` (password is stored in `/etc/shadow`)
- **UID**: `0` (root user, which has full system privileges)
- **GID**: `0` (root group)
- **Comment**: `root`
- **Home Directory**: `/root`
- **Shell**: `/bin/bash` (root can log in and use the bash shell)

### 2. `ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin`
- **Username**: `ftp`
- **Password**: `x`
- **UID**: `14`
- **GID**: `50`
- **Comment**: `FTP User` (a user for FTP services)
- **Home Directory**: `/var/ftp`
- **Shell**: `/sbin/nologin` (this user cannot log in interactively)

### 3. `rohail:x:1000:1000:Rohail Rathore:/home/rohail:/bin/bash`
- **Username**: `rohail`
- **Password**: `x`
- **UID**: `1000` (this is a regular user account)
- **GID**: `1000` (primary group is also `rohail`)
- **Comment**: `Rohail Rathore`
- **Home Directory**: `/home/rohail`
- **Shell**: `/bin/bash` (this user can log in and use the bash shell)

## Key Insights:
- System accounts like `bin`, `daemon`, and `mail` typically have the shell set to `/sbin/nologin` to prevent interactive logins, as they are used for system services.
- User accounts like `rohail` have the shell set to `/bin/bash`, meaning the user can log in and interact with the system using the Bash shell.
- The **UID** and **GID** values determine the user's permissions and access levels on the system. System users typically have lower UIDs, while regular users like `rohail` have UIDs starting from `1000`.


---
```
-rw-rw-r--. 1 rohail rohail  0 Oct 12 07:13 file3
```

## Breakdown of Each Field

1. **File Type and Permissions (`-rw-rw-r--.`)**:
   - **`-`**: Indicates that this is a regular file (as opposed to a directory, which would be `d`).
   - **`rw-`**: The owner's permissions (in this case, `rohail`):
     - `r`: Read permission (owner can read the file)
     - `w`: Write permission (owner can write to the file)
     - `-`: No execute permission (owner cannot execute the file)
   - **`rw-`**: The group's permissions (same as the owner):
     - `r`: Read permission (group can read the file)
     - `w`: Write permission (group can write to the file)
     - `-`: No execute permission (group cannot execute the file)
   - **`r--`**: Permissions for others (users not in the owner or group):
     - `r`: Read permission (others can read the file)
     - `-`: No write permission (others cannot write to the file)
     - `-`: No execute permission (others cannot execute the file)
   - **`.`**: Indicates that SELinux is enabled and may have additional security context.

2. **Link Count (`1`)**:
   - The number of hard links to the file. In this case, there is one link.

3. **Owner (`rohail`)**:
   - The username of the file's owner.

4. **Group (`rohail`)**:
   - The name of the group that owns the file.

5. **File Size (`0`)**:
   - The size of the file in bytes. Here, `file3` is empty (0 bytes).

6. **Modification Date and Time (`Oct 12 07:13`)**:
   - The date and time when the file was last modified. In this case, the file was last modified on October 12 at 07:13.

7. **File Name (`file3`)**:
   - The name of the file.

## Summary

This line provides a detailed view of the file's permissions, ownership, size, modification date, and file name, which is essential for managing access and understanding file attributes in a Linux environment.
```


