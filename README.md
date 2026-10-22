<div align="center">

# 🐧 Linux for Cloud Engineers

### My daily learning journal: from zero to cloud-ready ☁️

![Linux](https://img.shields.io/badge/Linux-Ubuntu_(WSL)-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Cloud](https://img.shields.io/badge/Goal-Cloud_Engineer-0078D4?style=for-the-badge&logo=icloud&logoColor=white)
![Status](https://img.shields.io/badge/Status-Learning_Daily-2ea44f?style=for-the-badge)
![Plan](https://img.shields.io/badge/Plan-15--20_Days-8957e5?style=for-the-badge)

*One day at a time. One command at a time.* 🚀

</div>

---

## 📅 Progress Tracker

| Day | Topic | Status |
|:---:|---|:---:|
| 1 | Navigation & Folders | ✅ Done |
| 2 | Copy, Move, Delete | ✅ Done |
| 3 | File Viewing, Logs & grep | ✅ Done |
| 4 | File Permissions | ✅ Done |
| 5 | Coming soon... | ⏳ Next |

> 📂 **Practice folder:** `~/cloud-lab` (WSL Ubuntu)

---

## 🧭 Day 1: Navigation & Folders

| Command | Syntax | What it does |
|---|---|---|
| 📍 `pwd` | `pwd` | Shows the directory you are currently in |
| 📃 `ls` | `ls` | Lists files and folders |
| 🔎 `ls -l` | `ls -l` | Lists with details (permissions, size, date) |
| 👻 `ls -a` | `ls -a` | Lists all files, including hidden ones |
| 🚪 `cd` | `cd folder/` | Moves into a folder |
| ⬆️ `cd ..` | `cd ..` | Moves one level up (parent folder) |
| 🏠 `cd ~` | `cd ~` | Goes to the home directory |
| 📁 `mkdir` | `mkdir name` | Creates a new folder |
| 🌳 `mkdir -p` | `mkdir -p a/b/c` | Creates nested folders in one go |
| 📄 `touch` | `touch file.txt` | Creates a new empty file |

---

## 📦 Day 2: Copy, Move, Delete

| Command | Syntax | What it does |
|---|---|---|
| 📋 `cp` | `cp source destination` | Copies a file (original stays unchanged) |
| 🗂️ `cp -r` | `cp -r folder1 folder2` | Copies an entire folder |
| 🚚 `mv` (move) | `mv file folder/` | Moves a file into another folder |
| ✏️ `mv` (rename) | `mv old.txt new.txt` | Renames a file |
| 🗑️ `rm` | `rm file.txt` | Deletes a file |
| 💣 `rm -r` | `rm -r folder` | Deletes a folder and its contents |
| 🧹 `rmdir` | `rmdir folder` | Deletes an empty folder only |
| 🔍 `find` | `find . -name "app.log"` | Searches for a file by name, starting from the current folder |
| 🌟 `find` (wildcard) | `find . -name "*.txt"` | Finds all files with a given extension |
| 🏷️ `file` | `file commands.txt` | Shows what type of file it is (text, empty, executable, etc.) |
| 📊 `stat` | `stat commands.txt` | Shows detailed metadata (size, permissions, owner, timestamps, inode) |
| 📍 `.` | `ls .` | Means the current directory |
| 🔀 `../folder` | `cd ../logs` | Goes up one level, then into a sibling folder |

**Example:** `cp linux/commands.txt backup/` then verify with `ls backup/`

> [!TIP]
> Always take a backup with `cp` before changing any config file.

> [!WARNING]
> Linux has no recycle bin. Once you run `rm`, the file is gone. Double-check before deleting!

---

## 🔍 Day 3: File Viewing, Logs & grep

| Command | Syntax | What it does |
|---|---|---|
| 🐱 `cat` | `cat file.log` | Prints the whole file (good for small files) |
| 📖 `less` | `less file.log` | Reads a large file page by page |
| ⬆️ `head` | `head -n 5 file.log` | Shows the first 5 lines (default 10) |
| ⬇️ `tail` | `tail -n 5 file.log` | Shows the last 5 lines (default 10) |
| 📡 `tail -f` | `tail -f file.log` | Follows the file and shows new lines live |
| 🎯 `grep` | `grep "ERROR" file.log` | Shows only lines containing the text |
| 🔢 `grep -n` | `grep -n "ERROR" file.log` | Shows matching lines with line numbers |
| 🔠 `grep -i` | `grep -i "error" file.log` | Ignores uppercase/lowercase |
| 🧮 `grep -c` | `grep -c "ERROR" file.log` | Counts matching lines |

> [!NOTE]
> `less` keys: `Space` next page, `b` previous page, `/ERROR` search, `n` next match, `q` quit.
> Stop `tail -f` with `Ctrl + C`.

### ✍️ Redirection (operators, not commands)

| Symbol | Example | What it does |
|:---:|---|---|
| `>` | `echo "hi" > a.txt` | **Replaces** the file's existing content |
| `>>` | `echo "hi" >> a.txt` | **Appends** to the end, keeping existing content |

### 🩺 Log Troubleshooting Flow

```text
Logs ➜ Service ➜ Network ➜ DNS ➜ Port ➜ Credentials
```

> [!IMPORTANT]
> "Database connection failed" does **not** automatically mean the DB server is down. Gather evidence first!

| Step | Command | What it tells you |
|---|---|---|
| 🛠️ Service | `sudo systemctl status mysql` | Whether the service is running |
| 🌐 Network | `ping <IP>` | Basic reachability (ICMP may be blocked) |
| 🧭 DNS | `nslookup <hostname>` | Whether the hostname resolves to an IP |
| 🔌 Port | `nc -vz <IP> 3306` | Whether a TCP connection to the port works |

<details>
<summary>🎤 <b>Interview Q&A (click to expand)</b></summary>

<br>

**Q: Difference between `cat` and `less`?**
`cat` prints the whole file at once. `less` lets you scroll through a large file page by page.

**Q: Difference between `head` and `tail`?**
`head` shows the beginning of a file, `tail` shows the end.

**Q: Difference between `>` and `>>`?**
`>` replaces the file content, `>>` appends to it.

**Q: How would you troubleshoot an app using logs?**
Check the logs with `grep` and `tail`, then verify the service, network, DNS, port and credentials before deciding the root cause.

</details>
---

## 🔐 Day 4: File Permissions

| Command | Syntax | What it does |
|---|---|---|
| 🙋 `whoami` | `whoami` | Shows the user running your current shell |
| 🔎 `ls -l` | `ls -l file.txt` | Shows permissions, owner and group of a file |
| 🔓 `chmod` | `chmod` | changes a file's permissions |
| 🔓 `chmod +x` | `chmod +x file` | Adds execute permission |
| 👤 `chmod u+x` | `chmod u+x deploy.sh` | Adds execute permission for the owner only |
| 🔢 `chmod 644` | `chmod 644 file` | Owner: read+write, group and others: read only |
| 🔒 `chmod 600` | `chmod 600 file` | Only the owner can read and write |
| 👑 `chown` | `sudo chown USER:GROUP file` | Changes the owner and group of a file |

### 📖 Permission types

| Symbol | Permission | On a file | On a directory |
|:---:|---|---|---|
| `r` | Read (4) | View contents | List entries |
| `w` | Write (2) | Modify contents | Create, delete, rename entries |
| `x` | Execute (1) | Run as a program/script | Enter (traverse) it |

**Who gets permissions:** `u` = User (owner), `g` = Group, `o` = Others

### 🧩 How to read `ls -l`

```text
-rw-r--r--  1  ekta  ekta  0  Oct 12  permissions-demo.txt
│└┬┘└┬┘└┬┘
│ │  │  └── Others: r--  (read only)
│ │  └───── Group:  r--  (read only)
│ └──────── Owner:  rw-  (read + write)
└────────── File type (- = file, d = directory)
```

### 🔢 Numeric mode (add the values)

| Number | Meaning | Calculation |
|:---:|---|---|
| 7 | rwx | 4+2+1 |
| 6 | rw- | 4+2 |
| 5 | r-x | 4+1 |
| 4 | r-- | 4 |

**Example:** `644` = owner `6` (rw-), group `4` (r--), others `4` (r--)

> [!WARNING]
> Don't fix every permission error with `chmod 777`. It gives everyone read, write and execute access and creates a security risk.

> [!NOTE]
> `chmod +x` only adds the permission. It does not turn a text file into a working script.

### 🩺 "Permission denied" troubleshooting flow

```text
ls -l file  ➜  whoami  ➜  chmod u+x file (if authorized)  ➜  run again
```

If it still fails, check the directory permissions, ownership, script interpreter and other security restrictions.

<details>
<summary>🎤 <b>Interview Q&A (click to expand)</b></summary>

<br>

**Q: What is the difference between r, w and x?**
`r` lets you read a file, `w` lets you modify it, and `x` lets you run it. On directories, `r` lists contents, `w` creates/deletes entries, and `x` allows entering the directory.

**Q: What does `chmod 644 file.txt` do?**
The owner gets read and write, while the group and others get read only.

**Q: An application gets "Permission denied" on a config file. What do you check first?**
I run `ls -l` on the file to see its permissions and owner, check which user the application runs as, and then check directory permissions before changing anything.

</details>

---

<div align="center">

⭐ *Learning in public. More days coming soon!* ⭐

</div>
