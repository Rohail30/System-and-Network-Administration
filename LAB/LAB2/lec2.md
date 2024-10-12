# File Permissions in Linux

In Linux, file and directory permissions are shown using a string like `drwxr-xr-x`. These strings represent the access rights for different users. Here's a breakdown:

## Structure of Permissions

The permission string `drwxr-xr-x` is divided into several parts:

- **First character**: Indicates the file type.
- **Next nine characters**: Represent the permissions for the user (owner), group, and others.

### 1. **File Type**
The first character specifies the type of the file:

- `d` : Directory
- `-` : Regular file
- `l` : Symbolic link
- `b` : Block device
- `c` : Character device
- `s` : Socket

### 2. **User Permissions (Owner)**
The first set of three characters (`rwx` in `drwxr-xr-x`) represents the permissions for the **file's owner** (user):

- `r` : Read permission
- `w` : Write permission
- `x` : Execute permission

### 3. **Group Permissions**
The second set of three characters (`r-x` in `drwxr-xr-x`) represents the permissions for the **group**:

- `r` : Read permission
- `w` : Write permission
- `x` : Execute permission

### 4. **Other Permissions (Everyone else)**
The third set of three characters (`r-x` in `drwxr-xr-x`) represents the permissions for **others** (everyone not in the user or group):

- `r` : Read permission
- `w` : Write permission
- `x` : Execute permission

### Example: `drwxr-xr-x`

- **d** : This is a directory.
- **rwx** : The owner (user) has read, write, and execute permissions.
- **r-x** : The group has read and execute permissions but cannot write.
- **r-x** : Others have read and execute permissions but cannot write.

---

## Summary of Permission Notation

| Symbol | Meaning  | Applies To |
|--------|----------|------------|
| `d`    | Directory| File Type  |
| `r`    | Read     | User, Group, Other |
| `w`    | Write    | User, Group, Other |
| `x`    | Execute  | User, Group, Other |
| `-`    | No permission | N/A     |


## Linux User and Permissions Cheat Sheet

## List Users and Groups:

* **`cat /etc/passwd`** - Lists all users on the system.
* **`cat /etc/group`** - Lists all groups on the system.

## User Management:

* **`sudo adduser testuser`** - Adds a new user to the system.
* **`sudo deluser testuser`** - Deletes a user from the system.
* **`sudo passwd testuser`** - Changes the password of a user.
* **`su -l testuser`** - Switches user account.
* **`sudo usermod -aG sudo testuser`** - Adds a user to the sudoers group.

## Group Management:

* **`sudo groupadd testgroup`** - Adds a new group to the system.
* **`sudo groupdel testgroup`** - Deletes a group from the system.
* **`sudo usermod -aG testgroup testuser`** - Adds a user to a group.
* **`sudo gpasswd -d testuser testgroup`** - Removes a user from a group.

## File and Directory Permissions:

* **`ls -l`** - Lists files in a long format (permissions, ownership, size, and modification date).

### Linux Permissions Annotations:

- `r` - Read
- `w` - Write
- `x` - Execute
- `-` - No permission
- `1` - Execute only
- `2` - Write only
- `3` - Write and execute
- `4` - Read only
- `5` - Read and execute
- `6` - Read and write
- `7` - Read, write, and execute
- `u` - User
- `g` - Group
- `o` - Others
- `a` - All

### Changing Permissions:

* **`chmod 777 myfile.txt`** - Gives all permissions to all users.
* **`chmod o+w myfile.txt`** - Gives write permission to others.
* **`chmod g-xw myfile.txt`** - Removes execute and write permissions from the group.

### Changing Ownership:

* **`chown testuser myfile.txt`** - Changes the ownership of a file.
* **`chown :testgroup myfile.txt`** - Changes the group of a file.
* **`chown testuser:testgroup myfile.txt`** - Changes the ownership of a file and group.
* **`chown -R testuser:testgroup myfolder`** - Changes the ownership of folders and subfolders recursively.

