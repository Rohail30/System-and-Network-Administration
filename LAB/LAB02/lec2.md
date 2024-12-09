# File Permissions in Linux

In Linux, file and directory permissions are shown using a string like `drwxr-xr-x`. These strings represent the access rights for different users. Here's a breakdown:



#### **Decoding `ls -l` Output**
The `ls -l` command provides detailed information about files and directories.

Example output:
```bash
-rw-rw-r-- 1 jason users 10400 Sep 27 08:52 sales.data
```
- **`-rw-rw-r--`**: Permissions
- **`1`**: Number of links
- **`jason`**: Owner
- **`users`**: Group
- **`10400`**: File size in bytes
- **`Sep 27 08:52`**: Last modification time
- **`sales.data`**: File name

#### **Useful `ls` Options**
| Option       | Description                               |
|--------------|-------------------------------------------|
| `-a`         | List all files, including hidden ones.    |
| `--color`    | Colorize output for better readability.   |
| `-d`         | List directory names, not contents.       |
| `-l`         | Use the long listing format.              |
| `-r`         | Reverse the order.                        |
| `-R`         | List files recursively.                   |
| `-t`         | Sort by time, most recent first.          |

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


## **Understanding Permissions**
Example file output from `ls -l`:
```bash
-rw-rw-r-- 1 jason users 10400 Sep 27 08:52 sales.data
```
- **Permissions Breakdown**:
  - First character (`-`): Type (`-` for file, `d` for directory, `l` for link).
  - Remaining characters (`rw-rw-r--`): Permissions:
    - `r` = Read
    - `w` = Write
    - `x` = Execute

- **Categories**:
  - `u` (User/Owner)
  - `g` (Group)
  - `o` (Others)

## **File vs. Directory Permissions**
| Permission | File Behavior                         | Directory Behavior                       |
|------------|---------------------------------------|------------------------------------------|
| `r`        | Read the file’s contents.             | List directory contents.                 |
| `w`        | Modify the file.                     | Add, remove, or rename files inside.     |
| `x`        | Execute the file as a program.       | Access directory and its metadata.       |


## **Changing Permissions**
Use `chmod` to change file or directory permissions.

- **Symbolic Format**:
  ```bash
  chmod u+x file  # Add execute permission for the user.
  chmod g-w file  # Remove write permission for the group.
  chmod o=r file  # Set read-only permission for others.
  ```

- **Numeric Format**:
  - Each permission is represented as a number:
    - `r=4`, `w=2`, `x=1`.
    - Example: `chmod 755 file` sets permissions to `rwxr-xr-x`.


## **Common Permission Modes**
| Symbolic    | Numeric | Description                      |
|-------------|---------|----------------------------------|
| `-rwx------`| `700`   | Owner has full access.           |
| `-rwxr-xr-x`| `755`   | Owner has full, others read/execute.|
| `-rw-rw-r--`| `664`   | Owner/group read/write, others read.|
| `-rw-r--r--`| `644`   | Owner read/write, others read.   |

## **Working with Groups**
- **Check Groups**:
  ```bash
  groups
  ```
- **Change File Group**:
  ```bash
  chgrp newgroup file
  ```


## **File Creation Mask**
- The **umask** command sets default permissions for new files and directories.
- Example:
  ```bash
  umask 022
  ```
  - Result:
    - Files: `644`
    - Directories: `755`


## **Special Modes**
1. **Setuid**: Run program with file owner’s permissions.
2. **Setgid**: Run program with file group’s permissions.
3. **Sticky Bit**: Restrict file deletion to the owner.

### **Summary Table**

| Mode       | Command to Set | Command to Remove | Description                                     |
|------------|----------------|-------------------|-------------------------------------------------|
| **Setuid** | `chmod u+s file` | `chmod u-s file` | Run with file owner’s permissions.             |
| **Setgid** | `chmod g+s file` | `chmod g-s file` | Run with file group’s permissions.             |
| **Sticky** | `chmod +t dir`   | `chmod -t dir`   | Restrict file deletion to the owner.           |

These modes are essential for managing permissions in multi-user environments. Let me know if you need further examples or explanations!

Set special modes with `chmod`:
```bash
chmod +s file  # Setuid/Setgid.
chmod +t dir   # Sticky bit.
```

# Linux User and Permissions Cheat Sheet

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

# Linux Command Line Notes

This document provides an overview of commonly used Linux commands and their functionalities.

## Basic Commands

- `~ls`: Lists files and directories in the current working directory.
- `~ls -l`: Lists files with detailed information including permissions, ownership, size, and modification time.
- `~ls -a`: Lists all files including hidden files (those starting with a dot).
- `~ls -al`: Lists all files (including hidden files) with detailed information.
- `~ls -ltr`: Lists files in long format, sorted by modification time in reverse order (newest last).
- `~ls -ltra`: Lists all files (including hidden) in long format, sorted by modification time in reverse order.
- `~grep folder`: Searches for the term "folder" within files or output.
- `~ls -ltra | grep folder`: Lists all files (including hidden), sorted by modification time, and filters the output for the term "folder".
- `~ls -C`: Lists files in columns.
- `~ls -ltrC`: Lists files in long format, sorted by modification time in reverse order, and displays them in columns.
- `~man ls`: Opens the manual (documentation) for the `ls` command.

## Navigating Directories

- `~cd /etc/sysconfig/`: Changes the current directory to `/etc/sysconfig/`.
- `~cd`: Changes the directory to the user's home directory.
- `~echo $OLDPWD`: Prints the previous working directory.
- `~printenv`: Prints all environment variables.

## Working with Files

- `~ls /bin`: Lists the contents of the `/bin` directory.
- `~echo "hello world 2" >> file`: Appends the string "hello world 2" to a file called `file`.
- `~cat file`: Displays the contents of the file `file`.
- `~which cat`: Shows the full path of the `cat` command.
- `~which more`: Shows the full path of the `more` command.

## Network & System Operations

- `ping 8.8.8.8`: Sends ICMP packets to the IP address `8.8.8.8` to test network connectivity.
- `su root`: Switches the user to the root account.
- `yum install tree`: Installs the `tree` package (used for viewing directory structures).

---


