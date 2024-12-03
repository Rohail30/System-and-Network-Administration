## **User and Group Management in Linux**

### **Key Concepts**

1. **User Accounts**:
   - A user account has the following components:
     - **Username (Login ID)**: Unique name used for login.
     - **UID (User ID)**: Unique number identifying the user.
     - **Default Group (GID)**: Primary group assigned to the user.
     - **Comments (GECOS Field)**: Optional metadata about the user (e.g., full name, phone number).
     - **Shell**: The program or command-line interface the user interacts with after login.
     - **Home Directory**: The default location where a user is placed after logging in.

---

### **Files Related to Users and Groups**

1. **/etc/passwd**:
   - Stores basic information about user accounts.
   - Format: `username:password:UID:GID:comments:home_dir:shell`
   - Example:  
     ```
     root:x:0:0:root:/root:/bin/bash
     ```
   - Everyone can read this file.

2. **/etc/shadow**:
   - Stores encrypted passwords.
   - Only readable by root for security.
   - Prevents regular users from attempting to crack passwords.

3. **/etc/group**:
   - Stores group information.
   - Format: `group_name:password:GID:account1,account2`
   - Example:
     ```
     sales:x:1001:john,mary
     ```

---

### **Managing Users**

#### **Adding Users**:
- Use the `useradd` command:
  ```bash
  useradd [options] username
  ```
- Common options:
  - `-c "COMMENT"`: Adds comments about the user.
  - `-m`: Creates a home directory.
  - `-s /path/to/shell`: Specifies the user's shell.
  - `-g GROUP`: Specifies the user's default group.
  - `-G GROUP1,GROUP2`: Assigns additional groups.
  - `-d /path/to/home`: Specifies a custom home directory.
  - `-u UID`: Sets a specific UID.

- Example:
  ```bash
  useradd -c "John Doe" -m -s /bin/bash -g sales -G devops jdoe
  ```

#### **Setting Passwords**:
- Use the `passwd` command:
  ```bash
  passwd username
  ```
- Example interaction:
  ```
  Enter new UNIX password:
  Retype new UNIX password:
  passwd: password updated successfully
  ```

#### **Deleting Users**:
- Use the `userdel` command:
  - Syntax:
    ```bash
    userdel [-r] username
    ```
  - `-r`: Removes the user’s home directory.
  - Example:
    ```bash
    userdel -r jdoe
    ```

#### **Modifying Users**:
- Use the `usermod` command:
  ```bash
  usermod [options] username
  ```
- Common options:
  - `-c "COMMENT"`: Updates comments.
  - `-g GROUP`: Changes the default group.
  - `-G GROUP1,GROUP2`: Adds user to additional groups.
  - `-s /path/to/shell`: Updates the user’s shell.
  - `-d /new/home/dir`: Changes the user’s home directory.
  - `-u UID`: Changes the UID.
- Example:
  ```bash
  usermod -c "Updated Name" -G editors,developers jdoe
  ```

---

### **Managing Groups**

#### **Adding Groups**:
- Use the `groupadd` command:
  - Syntax:
    ```bash
    groupadd [options] group_name
    ```
  - `-g GID`: Specifies a custom GID.
  - Example:
    ```bash
    groupadd -g 2001 project_team
    ```

#### **Deleting Groups**:
- Use the `groupdel` command:
  ```bash
  groupdel group_name
  ```
- Example:
  ```bash
  groupdel project_team
  ```

#### **Modifying Groups**:
- Use the `groupmod` command:
  ```bash
  groupmod [options] group_name
  ```
  - `-g GID`: Changes the group ID.
  - `-n NEW_NAME`: Renames the group.
- Example:
  ```bash
  groupmod -g 2500 -n dev_group developers
  ```

---

### **System and Application Accounts**

1. **System Accounts**:
   - Used for services or applications.
   - Created using:
     ```bash
     useradd -r -d /opt/app_dir -s /usr/sbin/nologin username
     ```
   - Example:
     ```bash
     useradd -r -d /opt/mysql -s /usr/sbin/nologin mysql
     ```

2. **Skeleton Directory**:
   - `/etc/skel`: Contains default files copied to new user home directories.
   - Example contents: `.bashrc`, `.profile`.

---

### **Groups and Permissions**

1. **Default Group**:
   - Each user is assigned a primary group (GID).
   - Default group affects the ownership of new files.

2. **Switching Groups**:
   - Users can temporarily switch groups using the `newgrp` command:
     ```bash
     newgrp group_name
     ```

3. **Viewing Groups**:
   - To list the groups a user belongs to:
     ```bash
     groups username
     ```
   - Example:
     ```bash
     groups jdoe
     ```

---

### **Special Details**

1. **Usernames**:
   - Conventionally lowercase.
   - Should be under 8 characters.
   - Avoid special characters.

2. **UIDs**:
   - Root account always has UID `0`.
   - System accounts usually have UIDs below `1000`.

3. **Shells**:
   - Default shells are listed in `/etc/shells`.
   - To disable login for an account, set the shell to `/usr/sbin/nologin` or `/bin/false`.

---

### **Example Commands for Practice**

1. **Create User and Assign Groups**:
   ```bash
   useradd -c "Alice Smith" -m -s /bin/bash -g writers -G tv alice
   passwd alice
   ```

2. **Delete a User**:
   ```bash
   userdel -r alice
   ```

3. **Modify Group Name and ID**:
   ```bash
   groupmod -g 2500 -n admin developers
   ```

4. **Create a System Account**:
   ```bash
   useradd -r -d /opt/apache -s /usr/sbin/nologin apache
   ```

---

### **Summary**

- User information is stored in `/etc/passwd` and `/etc/shadow`.
- Groups are defined in `/etc/group`.
- Commands:
  - **User Commands**:
    - `useradd`, `passwd`, `userdel`, `usermod`
  - **Group Commands**:
    - `groupadd`, `groupdel`, `groupmod`
- Follow naming conventions for usernames and ensure secure password management.

---

