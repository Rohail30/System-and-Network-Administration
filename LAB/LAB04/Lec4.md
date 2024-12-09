# Searching, Redirection, and File Comparison

## Searching

### `grep` - Search for a pattern in a file:
```bash
grep "pattern" filename
```
- **`-i`**: Ignore case.
- **`-r`**: Search recursively in directories.
- **`-n`**: Display line numbers where matches are found.

### Example:
```bash
grep "error" logfile.txt
```

## Redirection

### Redirect output to a file:

#### Overwrite the file:
```bash
command > filename
```

#### Append to the file:
```bash
command >> filename
```

### Example:
```bash
echo "Hello, World!" > file.txt   # Overwrites the file
echo "Append this line" >> file.txt  # Appends to the file
```

## `diff` - Compare files

### `diff` Command Syntax:
```bash
diff file1 file2
```

- **`-u`**: Unified format for the difference.
- **`-c`**: Context format.
- **`-i`**: Ignore case differences.

### Example:
```bash
diff file1.txt file2.txt
```
