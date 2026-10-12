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
| 4 | Coming soon... | ⏳ Next |

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

<div align="center">

⭐ *Learning in public. More days coming soon!* ⭐

</div>
