# `umask` in Linux

**`umask`** (short for "user file creation mask") is a Linux/Unix command and setting that determines the default permissions for newly created files and directories. It essentially defines a mask that restricts or modifies the default permissions assigned to files and directories when they are created.

## Default Permissions

When a file or directory is created, it is assigned a default set of permissions. These defaults are:
- **Files**: `666` (read and write for everyone)
- **Directories**: `777` (read, write, and execute for everyone)

The `umask` value subtracts certain permissions from these defaults, effectively setting the final permissions for the created files and directories.

## How `umask` Works

`umask` uses an octal (numeric) value to determine which permission bits should be disabled or "masked out." The value you set for `umask` is subtracted from the default permission values.

### Common Default `umask` Values:

1. **`022`**:
   - **Files**: `666 - 022 = 644` (read and write for the owner, read-only for group and others)
   - **Directories**: `777 - 022 = 755` (read, write, and execute for the owner, read and execute for group and others)
   
2. **`027`**:
   - **Files**: `666 - 027 = 640` (read and write for the owner, read-only for the group, no permissions for others)
   - **Directories**: `777 - 027 = 750` (read, write, and execute for the owner, read and execute for the group, no permissions for others)

3. **`077`**:
   - **Files**: `666 - 077 = 600` (read and write for the owner, no permissions for group and others)
   - **Directories**: `777 - 077 = 700` (read, write, and execute for the owner, no permissions for group and others)

## Command to Check `umask`

To check the current `umask` value, use:

```bash
umask
```

## Setting `umask`

To set a `umask` value, you can run:

```bash
umask 022
```

This command would set the `umask` to `022`, meaning that new files will be created with `644` permissions and new directories with `755` permissions.

## Example

Let’s say you have the following `umask` value:

```bash
umask 027
```

- When you create a **file**, the system subtracts `027` from the default file permission (`666`), resulting in a permission of `640`. This means the owner will have read and write permissions, the group will have read-only permission, and others will have no permissions.
  
- When you create a **directory**, the system subtracts `027` from the default directory permission (`777`), resulting in a permission of `750`. This means the owner can read, write, and execute; the group can read and execute; others have no permissions.

## Practical Usage

`umask` is important for system security and privacy. It ensures that newly created files and directories don’t have too permissive access rights, preventing unauthorized users from reading, writing, or executing them.

## Summary

- **`umask`** controls the default permissions for new files and directories.
- It "masks" certain permission bits, removing them from the default.
- A common `umask` value like `022` ensures that new files are `644` (read/write for the owner, read-only for others) and directories are `755` (read/write/execute for the owner, read/execute for others).



# Linux Commands 

## Removing Files
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

