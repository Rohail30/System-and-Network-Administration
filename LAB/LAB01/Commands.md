# CentOS 

## CentOS Overview
CentOS (Community ENTerprise Operating System) is a free, open-source Linux distribution based on Red Hat Enterprise Linux (RHEL). It offers full compatibility with RHEL without subscription costs and is commonly used for web hosting, cloud computing, and enterprise applications due to its stability and long-term support.

## `su root` Command
The subtitute user `su` command in CentOS lets users switch to the root (administrator) account, which has full system privileges for tasks like software installation, file management, and system configuration.

### Command Syntax:
```
su root
```

```
$ su root
Password: ********
#
```
Once logged in as root, you can perform administrative tasks like installing packages or modifying system settings.

## Shell and System Commands

### Basic Shell Commands
1. `exit` - Exits the current shell session.
2. `ls` - Lists files and directories in the current directory.
3. `pwd` - Displays the current working directory path.
4. `cd` - Changes the current working directory.
5. `man` - Displays the manual or help for a command.

### Relative Directories
1. `.` - Refers to the current directory.
2. `..` - Refers to the parent directory.
3. `~` - Refers to the home directory.
4. `~username` - Refers to the home directory of the specified user.
5. `~/Desktop` - Refers to the Desktop directory inside the home folder.

### Directory Management Commands
1. `ls` - Lists files and directories.
2. `pwd` - Prints the current directory path.
3. `cd` - Changes the working directory.
4. `mkdir` - Creates a new directory.
5. `rmdir` - Removes an empty directory.

### Shell/System Commands
1. `man` or `info` - Shows the manual pages for commands.
2. `clear` - Clears the terminal screen.
3. `exit` - Closes the shell session.
4. `date` - Displays or sets the system date and time.
5. `cal` - Displays a calendar for a month or a year.
6. `uname` - Displays system information (e.g., OS name).

### File Commands
1. `cp` - Copies files or directories.
2. `mv` - Moves or renames files or directories.
3. `rm` - Removes (deletes) files or directories.
4. `touch` - Creates a new empty file or updates the timestamp of an existing file.

## More Linux Commands with Format

### Removing Files
- **`rm file`**: Remove a specified file.
- **`rm -r dir`**: Remove the directory and its contents recursively.
- **`rm -f file`**: Force removal of a file and never prompt for confirmation.

### Example Usage
```bash
$ ls s*
sales-lecture.mp3 sales.data secret secret.bak
$ rm s*
$ ls -d .*
. .. .profile .bash_history
$ rm .*
rm: cannot remove ‘.’: Is a directory
rm: cannot remove ‘..’: Is a directory
$ ls -d .*
. ..
```

## Copying Files
- **`cp source_file destination_file`**: Copy `source_file` to `destination_file`.
- **`cp src_file1 [src_fileN ...] dest_dir`**: Copy multiple `source_files` to `destination_directory`.

### Options
- **`cp -i`**: Run in interactive mode, prompting before overwrite.
- **`cp -r source_directory destination`**: Copy `source_directory` recursively to `destination`.

## Moving and Renaming Files
- **`mv`**: Move or rename files and directories.
- **`mv source destination`**: Move or rename a file or directory.
- **`mv -i source destination`**: Move with interactive prompt before overwrite.

## Sorting Data
- **`sort file`**: Sort text in a specified file.

### Options
- **`-k F`**: Sort by key, where `F` is the field number.
- **`-r`**: Sort in reverse order.
- **`-u`**: Sort unique values.

## Creating a Collection of Files
- **`tar [-] c|x|t f tarfile [pattern]`**: Create, extract, or list contents of a tar archive using an optional pattern.

### Options
- **`c`**: Create a tar archive.
- **`x`**: Extract files from the archive.
- **`t`**: Display the table of contents (list).
- **`v`**: Be verbose in output.
- **`z`**: Use compression.
- **`f file`**: Use the specified file.

## Compressing Files To Save Space
- **`gzip`**: Compress files.
- **`gunzip`**: Uncompress files.
- **`gzcat`**: Concatenate compressed files.
- **`zcat`**: Another way to concatenate compressed files.

## Disk Usage
- **`du`**: Estimates file usage.
- **`du -k`**: Display sizes in Kilobytes.
- **`du -h`**: Display sizes in human-readable format.


