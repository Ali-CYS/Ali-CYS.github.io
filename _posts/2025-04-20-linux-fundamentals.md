---
title: "LAN & Topologiess"
date: 2025-04-16 15:42:00 +0500
categories: [Security-Basics,Linux]
tags: [Linux]
mermaid: true
comments: true
---

# Linux Fundamentals

## Commands

### Basic Commands

- **echo** → Used to store text in another file.
    
    ```bash
    echo "hello" > hell.txt
    ```
    
- **whoami** → Find out who is logged in.
    
- **ls** → List all contents of a directory.
    
- **cd** → Change the directory.
    
- **cat** → Display the text in a `.txt` file.
    
- **pwd** → Show the current directory path.
    
- **find** → Find a file in the system.
    
    - If we know the name:
        
        ```bash
        find -name password.txt
        ```
        
    - If we don’t know the file name:
        
        ```bash
        find -name "*.txt"
        ```
        
        - This searches for all `.txt` files.
- **grep** → Search for text in a file.
    
    ```bash
    grep 'file/text' filename
    ```
    
---

### Operators

- **`&` operator** → Runs a program in the background.
    
- **`&&` operator** → Runs two programs together, but the second program runs only if the first one is successful.
    
- **`>` operator** → Takes output and directs it somewhere.
    
    ```bash
    echo "hello" > new.txt
    ```
    
    - This overwrites existing content in `new.txt`.
- **`>>` operator** → Similar to `>`, but does not overwrite existing content.
    
    ```bash
    echo "hello" >> new.txt
    ```
    
     - This appends text to `new.txt` instead of overwriting it.

---

### File and Directory Management

- **mv** → Moves a file.
    
    ```bash
    mv note10 note11
    ```
    
    - `note11` now contains the content of `note10`.
- **file** → Determines the file type.
    
- **SSH** → Secure shell command to connect to a remote machine.
    
    ```bash
    ssh username@IPaddress
    ```
    
- **Flags/Switches** → Modify command behavior.
    
    ```bash
    ls -a
    ```
    
    - `-a` lists all files, including hidden ones.
    
    ```bash
    ls --help
    ```
    
    - Displays available flags for `ls`.
    
    ```bash
    man ls
    ```
    
    - Opens the manual page for `ls`.
- **touch** → Creates a new file.
    
    ```bash
    touch notes
    ```
    
- **mkdir** → Creates a new directory.
    
    ```bash
    mkdir my_directory
    ```
    
- **rm** → Removes a file.
    
    ```bash
    rm filename
    ```
    
- **cp** → Copies a file.
    
    ```bash
    cp source.txt destination.txt
    ```
    
---
### File Permissions

- **Permissions (read, write, execute)**
    
    ```bash
    ls -lh
    ```
    
    - Shows file permissions for the current user.

### Common Directories

- **/etc** → Root directory
    
    - Contains passwords encrypted using SHA-512.
- **/var** → Stores variable data.
    
    - Used for storing application data running on the system.
    - Example: `/var/log` → Contains log files.
- **/root** → Home for the root system user.
    
- **/tmp** → Temporary file storage.
    
    - Stores data that needs to be accessed temporarily.
    - Data clears on restart.
    - Useful for persisting as users can write to it.

---
### **Terminal Text Editors**

#### **1) Nano**

```
nano "File name"
```

#### **2) Vim**

```
vim "File name"
```

- More advanced text editor
- Many cheatsheets easily available

---

### **wget**

Used to download anything.

```
wget "File URL/link"
```

---

### **SCP (Secure Copy)**

- Different from the regular `cp` command

**Copy a file to a remote machine:**

```
scp important.txt machine_IP
```

**Copy a file from a remote machine:**

```
scp machine_IP important.txt
```

### **Process View**

- **ps** → Check what is running and its usage.
- **ps aux** → See programs run by other users as well.

---

### **Kill**

We can kill a process by its PID number:

```
kill PID_number
```

Some signals (commands) can be used:

- **SIGTERM** → Kills the process but allows it to do cleanup tasks.
- **SIGKILL** → Forcefully kills the process.
- **SIGSTOP** → Stops or suspends the process.

---


### **Process to Start on Boot**

- Some applications can be started on boot of the system we own. We use this command:
    
    ```
    systemctl [option] [service]
    ```
    
    Options can be:
    
    - **Disable**
    - **Start**
    - **Stop**
    - **Enable**

---

### **System Automation - Cron Jobs**

- `crontab -e`
- Automate different tasks
- Use online websites to create such cron process commands

---

### **APT Package Management**

- **`sudo apt update`** → Brings list of latest update packages available
- **`sudo apt install`** → Installs a package
- **`sudo apt upgrade`** → Downloads new package updates

---
