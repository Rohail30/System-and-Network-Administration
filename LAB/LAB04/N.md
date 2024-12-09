### Comprehensive Notes from Provided Files

---

## **File: Wildcards**
### **What You Will Learn**
- Wildcards: What they are, when and where they can be used.
- Types of wildcards and their usage in commands.

---

### **Wildcards Overview**
- **Definition**: Characters or strings used for pattern matching.
- **Globbing**: Expands the wildcard pattern into a list of matching files/directories.
- **Usage**: Can be used with commands like `ls`, `rm`, `cp`, etc.

---

### **Types of Wildcards**

1. **Asterisk (*)**  
   - Matches **zero or more characters**.  
   - Examples:
     - `*.txt` matches all `.txt` files.
     - `a*` matches all files starting with `a`.

2. **Question Mark (?)**  
   - Matches **exactly one character**.  
   - Examples:
     - `?.txt` matches files with one character before `.txt`.
     - `a?.txt` matches files starting with `a` followed by any one character.

3. **Character Classes ([])**  
   - Matches **one of the specified characters** in brackets.  
   - Examples:
     - `[aeiou]` matches vowels.
     - `ca[nt]*` matches `can`, `cat`, `candy`, `catch`.

4. **Negated Character Classes ([!])**  
   - Matches **any character NOT in the brackets**.  
   - Examples:
     - `[!aeiou]*` matches strings starting with non-vowel characters like `baseball`.

5. **Ranges ([a-z], [0-9])**  
   - Specify a range of characters using a hyphen.  
   - Examples:
     - `[a-g]*` matches files starting with letters `a` to `g`.
     - `[3-6]*` matches files starting with numbers `3` to `6`.

6. **Named Character Classes**  
   - Predefined patterns for character types.  
   - Examples:
     - `[[:alpha:]]` matches alphabetic characters.
     - `[[:digit:]]` matches numbers.
     - `[[:lower:]]` matches lowercase letters.
     - `[[:upper:]]` matches uppercase letters.
     - `[[:space:]]` matches whitespace.

7. **Escape Character (`\`)**  
   - Used to match wildcard characters literally.  
   - Example:
     - `*\?` matches files ending with a `?`.

---

### **Summary**
- Common wildcards: `*`, `?`, `[]`, `[!...]`, `[a-z]`, `[[:digit:]]`.

---

## **File: I/O Redirection**
### **What You Will Learn**
- Types of input/output (I/O).
- How to redirect input/output effectively.

---

### **Types of I/O**

| **I/O Name**       | **Abbreviation** | **File Descriptor** |
|---------------------|------------------|----------------------|
| **Standard Input**  | `stdin`         | `0`                  |
| **Standard Output** | `stdout`        | `1`                  |
| **Standard Error**  | `stderr`        | `2`                  |

---

### **Redirection Basics**

1. **Standard Output (`stdout`)**:
   - Redirect to a file (overwrites existing content):
     ```bash
     command > file
     ```
   - Append to a file:
     ```bash
     command >> file
     ```

2. **Standard Input (`stdin`)**:
   - Redirect input from a file:
     ```bash
     command < file
     ```

3. **Standard Error (`stderr`)**:
   - Redirect errors to a file:
     ```bash
     command 2> file
     ```

4. **Combine `stdout` and `stderr`**:
   - Redirect both to a single file:
     ```bash
     command > file 2>&1
     ```
   - Redirect both to `/dev/null` (discard output):
     ```bash
     command > /dev/null 2>&1
     ```

---

### **The Null Device**
- **`/dev/null`**: A special file that discards all data written to it.  
- Use case:
  - Suppress unwanted output:
    ```bash
    ls here not-here > /dev/null 2>&1
    ```

---

### **Summary**
- Standard I/O: `stdin`, `stdout`, `stderr`.
- Redirection operators: `>`, `>>`, `<`, `2>`, `2>&1`.
- Use `/dev/null` to discard unwanted output.

---

## **File: Comparing Files**
### **What You Will Learn**
- How to compare the contents of files using different commands.

---

### **Commands for File Comparison**

1. **`diff`**:
   - Compares two files line by line.
   - Syntax:
     ```bash
     diff file1 file2
     ```
   - Output:
     - Example:
       ```
       3c3
       < this is a line in a file.
       ---
       > This is a Line in a File!
       ```
     - **`<`**: Line from `file1`.  
     - **`>`**: Line from `file2`.  
     - **Actions**:
       - `A` = Add, `C` = Change, `D` = Delete.

2. **`sdiff`**:
   - Displays side-by-side comparisons.
   - Syntax:
     ```bash
     sdiff file1 file2
     ```
   - Output:
     ```
     line in file1  |  line in file2
         > more in file2
     ```

3. **`vimdiff`**:
   - Highlights differences using the `vim` editor.
   - Syntax:
     ```bash
     vimdiff file1 file2
     ```
   - Navigation:
     - `Ctrl-w w`: Switch between windows.
     - `:q`: Quit current window.
     - `:qa`: Quit all windows.
     - `:qa!`: Force quit all.

---

### **Summary**
- Tools for comparison:
  - `diff`: Line-by-line comparison.
  - `sdiff`: Side-by-side comparison.
  - `vimdiff`: Visual comparison in `vim`.

--- 

Let me know if you'd like further explanations or examples for any of these topics!
