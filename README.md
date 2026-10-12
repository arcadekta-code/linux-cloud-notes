# Linux for Cloud Engineers: Daily Notes

Practice folder: `~/cloud-lab` (WSL Ubuntu)

---

## Day 1: Navigation & Folders

| Command | Syntax | Meaning |
|---|---|---|
| pwd | `pwd` | Shows the current directory you are in |
| ls | `ls` | Lists files and folders in the current directory |
| ls -l | `ls -l` | Lists with details (permissions, size, date) |
| ls -a | `ls -a` | Lists all files, including hidden ones |
| cd | `cd folder/` | Moves into a folder |
| cd .. | `cd ..` | Moves one level up (parent folder) |
| cd ~ | `cd ~` | Goes to the home directory |
| mkdir | `mkdir name` | Creates a new folder |
| mkdir -p | `mkdir -p a/b/c` | Creates nested folders in one go |
| touch | `touch file.txt` | Creates a new empty file |

---

## Day 2: Copy, Move, Delete

| Command | Syntax | Meaning |
|---|---|---|
| cp | `cp source destination` | Copies a file (the original stays unchanged) |
| cp -r | `cp -r folder1 folder2` | Copies an entire folder |
| mv (move) | `mv file folder/` | Moves a file into another folder |
| mv (rename) | `mv old.txt new.txt` | Renames a file |
| rm | `rm file.txt` | Deletes a file (no recycle bin) |
| rm -r | `rm -r folder` | Deletes a folder and its contents |
| rmdir | `rmdir folder` | Deletes an empty folder only |

Example: `cp linux/commands.txt backup/`, then verify with `ls backup/`.
Tip: Take a backup with `cp` before changing any config file.

---

## Day 3: File Viewing, Logs & grep

| Command | Syntax | Meaning |
|---|---|---|
| cat | `cat file.log` | Prints the whole file on screen (good for small files) |
| less | `less file.log` | Reads a large file page by page |
| head | `head -n 5 file.log` | Shows the first 5 lines (default 10) |
| tail | `tail -n 5 file.log` | Shows the last 5 lines (default 10) |
| tail -f | `tail -f file.log` | Follows the file and shows new lines live (stop with `Ctrl + C`) |
| grep | `grep "ERROR" file.log` | Shows only the lines that contain the search text |
| grep -n | `grep -n "ERROR" file.log` | Shows matching lines with line numbers |
| grep -i | `grep -i "error" file.log` | Ignores uppercase/lowercase difference |
| grep -c | `grep -c "ERROR" file.log` | Counts the matching lines |

**`less` keys:** `Space` = next page, `b` = previous page, `/ERROR` = search, `n` = next match, `q` = quit

**Redirection (operators, not commands):**

| Symbol | Example | Meaning |
|---|---|---|
| `>` | `echo "hi" > a.txt` | Replaces the file's existing content with the new text |
| `>>` | `echo "hi" >> a.txt` | Keeps existing content and adds the new text at the end |

**Log troubleshooting flow:** Logs → Service → Network → DNS → Port → Credentials

A "Database connection failed" error does not automatically mean the DB server is down. Gather evidence first:

| Check | Command | What it tells you |
|---|---|---|
| Service | `sudo systemctl status mysql` | Whether the service is running |
| Network | `ping <IP>` | Basic reachability (ICMP may be blocked) |
| DNS | `nslookup <hostname>` | Whether the hostname resolves to an IP |
| Port | `nc -vz <IP> 3306` | Whether a TCP connection to the port succeeds |
