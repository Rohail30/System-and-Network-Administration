# CentOS System and Network Administration - Basic Commands

In this guide, we cover some essential CentOS commands learned in the System and Network Administration class.

## 1. `su root`
The `su` command stands for "substitute user" and is used to switch to another user. The most common use is switching to the root user to gain administrative privileges.

```bash
~ su root
password:
```
- After entering the `su root` command, you will be prompted for the root password. Once entered, your shell prompt changes, indicating you have root access.

## 2. `cd` - Change Directory
The `cd` command is used to navigate between directories.

### Example 1:
```bash
# cd
# pwd
```
- `cd`: Navigates to the current user's home directory.
- `pwd`: Prints the working directory. This confirms your current location in the file system.

### Example 2:
```bash
# cd /
# pwd
```
- `cd /`: Changes to the root directory.
- `pwd`: Verifies that the current directory is `/`.

### Example 3:
```bash
# cd /home/
# pwd
```
- `cd /home/`: Navigates to the `/home/` directory.
- `pwd`: Confirms your location as `/home/`.

### Example 4:
```bash
# cd ..
# pwd
```
- `cd ..`: Moves up one directory level.
- `pwd`: Verifies your current directory after moving up.

### Example 5:
```bash
# cd ~
# pwd
```
- `cd ~`: Navigates back to the current user’s home directory.
- `pwd`: Prints the working directory to verify your location.

## 3. `cat` - View File Content
The `cat` command is used to display the contents of a file. In this case, it is used to read system configuration files.

```bash
# cat /etc/passwd
```
- Displays the contents of the `/etc/passwd` file, which contains user account information on the system.

## 4. Navigating to Specific Directories

```bash
# cd /etc/sysconfig/
```
- This command moves to the `/etc/sysconfig/` directory, which contains configuration files for various system services.

---

These commands form the foundation of basic system navigation and file manipulation in CentOS, essential for managing and administering the system effectively.
```

