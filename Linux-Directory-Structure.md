### Linux Directory Structure - Simplified Notes

---

#### **Why Learn the Linux Directory Structure?**
- **Efficient Navigation**: Quickly find files and directories.  
- **Save Time**: Locate system components without confusion.  
- **Better Troubleshooting**: Understand where problems may arise.  
- **Enhanced Skills**: Be a more effective Linux user or administrator.  

---

### **Key Directories and Their Purpose**

1. **`/` (Root Directory)**  
   - The starting point of the Linux file system.  
   - Everything else is stored inside or linked here.  
   - Similar to "C:\" on Windows.

2. **`/bin` (Binaries)**  
   - Contains essential system commands and programs.  
   - Examples: `ls`, `cp`, `mv`.

3. **`/etc` (Configuration Files)**  
   - Stores configuration files for the system and applications.  
   - Examples: 
     - Network settings.
     - User account details.

4. **`/home` (Home Directories)**  
   - Stores personal files and settings for each user.  
   - Example: `/home/john` for user "John".  
   - Similar to "Documents and Settings" in Windows.

5. **`/opt` (Optional Software)**  
   - Holds third-party or manually installed software.  
   - Example: `/opt/google/chrome`.

6. **`/tmp` (Temporary Files)**  
   - Temporary storage for files.  
   - Automatically cleared after reboot.

7. **`/usr` (User Programs)**  
   - Contains system software and libraries used by all users.  
   - Examples:
     - `/usr/bin`: Additional executables (non-essential tools).  
     - `/usr/lib`: Libraries used by programs.  
     - `/usr/local`: Software installed manually by the user.

8. **`/var` (Variable Data)**  
   - Stores files that change often.  
   - Examples:
     - `/var/log`: System logs.
     - `/var/tmp`: Temporary data that persists after reboot.

---

### **Additional Important Directories**

1. **`/boot`**  
   - Holds bootloader and kernel files needed to start the system.  
   - Example: GRUB bootloader files.

2. **`/dev` (Devices)**  
   - Represents hardware devices like disks, printers, and USB drives.  
   - Example: `/dev/sda` for the first hard drive.

3. **`/lib` and `/lib64` (Libraries)**  
   - Essential libraries for system programs.  
   - `/lib64` is for 64-bit systems.

4. **`/media` and `/mnt`**  
   - Mount points for external devices like USB drives and CDs.  
   - Example: `/media/usb`.

5. **`/proc` (Processes)**  
   - Virtual directory that provides real-time information about running processes.  
   - Example: `/proc/cpuinfo` shows CPU details.

6. **`/root` (Root User’s Home)**  
   - Home directory for the `root` (admin) user.  
   - Separate from `/home`.

7. **`/srv` (Service Data)**  
   - Contains data served by system services like web or FTP servers.  
   - Example: `/srv/www` for web server files.

8. **`/sys`**  
   - Provides information about hardware connected to the system.  
   - Example: `/sys/block` for storage devices.

9. **`/lost+found`**  
   - Used to recover files during system checks.  
   - Found in each disk's root directory (e.g., `/lost+found`).

---

### **Where Applications Are Stored**

1. **Default Application Locations**:
   - System tools: `/bin`, `/usr/bin`, `/sbin`.  
   - Libraries: `/lib`, `/usr/lib`.

2. **Third-Party Applications**:
   - Installed in `/opt` or `/usr/local`.  
   - Example for a custom app:
     - `/usr/local/myapp/bin`: Executable files.
     - `/usr/local/myapp/lib`: Libraries.

3. **Examples of Applications**:
   - Chrome: `/opt/google/chrome`.  
   - Custom tools: `/usr/local/bin`.

---

### **Quick Reference Table**

| Directory     | Purpose                                               |
|---------------|-------------------------------------------------------|
| `/`           | Root of the file system.                              |
| `/bin`        | Essential commands (e.g., `ls`, `cat`).               |
| `/etc`        | System and application configuration files.           |
| `/home`       | User files and settings.                              |
| `/opt`        | Optional, third-party software.                       |
| `/tmp`        | Temporary files, cleared on reboot.                   |
| `/usr`        | Programs, libraries, and user-level software.         |
| `/var`        | Variable data (logs, caches).                         |
| `/boot`       | Bootloader and kernel files.                          |
| `/dev`        | Device files (hardware).                              |
| `/lib`        | Shared libraries for system programs.                 |
| `/media`      | Mount point for external devices.                     |
| `/mnt`        | Temporary mount point for file systems.               |
| `/proc`       | Information about processes.                          |
| `/root`       | Home directory for the root user.                     |
| `/srv`        | Data for system services.                             |
| `/sys`        | Hardware-related information.                         |
| `/lost+found` | Recovery folder for file system issues.               |

---

### **Key Points to Remember**

1. **Root (`/`) is the base**: Everything starts here.  
2. **System tools and libraries**: `/bin`, `/lib`, `/usr`.  
3. **User-specific files**: Found in `/home`.  
4. **Temporary and variable data**: Stored in `/tmp` and `/var`.  
5. **Third-party apps**: Installed in `/opt` or `/usr/local`.

---
