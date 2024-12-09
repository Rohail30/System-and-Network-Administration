## **1. Viewing and Editing Files**

### **Viewing File Contents**
- **cat file**: Displays the file content in one go.
  - Example: `cat file.txt`
- **more file**: Allows scrolling through the file (one screen at a time).
  - Commands: Press `Space` for the next page, `q` to quit.
  - Example: `more file.txt`
- **less file**: Similar to `more` but supports backward navigation.
  - Commands: Use `↑/↓` for navigation, `q` to quit.
  - Example: `less file.txt`
- **head file**: Displays the first 10 lines (default).
  - Example: `head -5 file.txt` (shows 5 lines).
- **tail file**: Displays the last 10 lines (default).
  - Example: `tail -15 file.txt` (shows 15 lines).

### **Real-Time File Viewing**
- **tail -f file**: Tracks changes in a file in real-time (useful for log monitoring).
  - Example: `tail -f /var/log/syslog`

---

## **2. Editing Files with Nano**
- **Nano Basics**
  - Simple and beginner-friendly.
  - Often available as the default text editor.

### **Common Nano Commands**
- **Save file**: `Ctrl-O`
- **Exit nano**: `Ctrl-X`
- **Search**: `Ctrl-W`, then type the search term.
- **Cut text**: `Ctrl-K`
- **Paste text**: `Ctrl-U`

---

## **3. Editing Files with Vi**
Vi is a powerful editor with modes:
- **Command Mode**: Default mode for navigation and commands.
- **Insert Mode**: For typing text (`i` to enter, `Esc` to exit).
- **Line Mode**: For saving, quitting, and other file operations.

### **Vi Navigation**
- `h`: Left | `j`: Down | `k`: Up | `l`: Right
- `w`: Next word | `b`: Previous word
- `^`: Start of the line | `$`: End of the line
- `gg`: First line | `G`: Last line | `:n`: Go to line `n`

### **Vi Inserting Text**
- `i`: Insert at cursor | `I`: At line start
- `a`: Append after cursor | `A`: Append at line end
- `o`: Open a new line below | `O`: Open above

### **Vi Deleting Text**
- `x`: Delete character | `dd`: Delete line | `dw`: Delete word

### **Vi Copy and Paste**
- `yy`: Copy line | `p`: Paste after cursor | `P`: Paste before cursor

### **Vi Save and Quit**
- `:w`: Save | `:q`: Quit | `:wq`: Save and quit
- `:q!`: Quit without saving | `:wq!`: Force save and quit

### **Vi Find and Replace**
- Search: `/pattern` (forward) | `?pattern` (reverse)
- Replace: `:s/old/new/` (current line)
  - Example: `:%s/old/new/g` (entire file)

---

### **Vi vs Nano**
| Feature          | Vi                  | Nano             |
|-------------------|---------------------|------------------|
| Learning Curve    | Steep               | Easy             |
| Navigation        | Advanced            | Simple           |
| Editing Modes     | Command, Insert, Line | Single Mode      |
| Features          | Highly customizable | Basic operations |

### Summary
- Vi is a powerful editor with extensive features but requires effort to learn.
- Nano is simple and easy for quick edits.
- Use file display commands like `cat`, `more`, `less`, `head`, and `tail` to view file content effectively.
