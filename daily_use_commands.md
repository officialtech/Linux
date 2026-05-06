# Linux CLI Commands - Daily Use Commands

---

## Table of Contents

1. [Navigation & File Management](#navigation--file-management)
2. [File Viewing & Editing](#file-viewing--editing)
3. [File Permissions & Ownership](#file-permissions--ownership)
4. [Searching & Finding](#searching--finding)
5. [Text Processing](#text-processing)
6. [System Information](#system-information)
7. [Process Management](#process-management)
8. [Networking](#networking)
9. [Compression & Archives](#compression--archives)
10. [User & Group Management](#user--group-management)
11. [Disk & Storage](#disk--storage)
12. [Package Management](#package-management)

---

## Navigation & File Management

Essential commands for moving around and managing files.

| Command | Purpose | Example |
|---------|---------|---------|
| `pwd` | Print working directory | `pwd` |
| `ls` | List files and folders | `ls -la` |
| `cd` | Change directory | `cd /home/user/documents` |
| `mkdir` | Create directory | `mkdir newfolder` |
| `rmdir` | Remove empty directory | `rmdir oldfolder` |
| `cp` | Copy file/folder | `cp file.txt /path/to/dest` |
| `mv` | Move/rename file | `mv oldname.txt newname.txt` |
| `rm` | Delete file | `rm file.txt` |
| `rm -r` | Delete directory recursively | `rm -r folder/` |
| `touch` | Create empty file | `touch newfile.txt` |
| `find` | Search for files | `find . -name "*.txt"` |

### Useful ls Options

```bash
ls -l              # Long format with details
ls -a              # Show hidden files
ls -h              # Human-readable file sizes
ls -S              # Sort by file size
ls -t              # Sort by modification time
ls -R              # Recursive (show subdirs)
ls -la             # Combine options
```

---

## File Viewing & Editing

Commands to read and modify file contents.

| Command | Purpose | Example |
|---------|---------|---------|
| `cat` | Display file contents | `cat file.txt` |
| `head` | Show first lines | `head -n 10 file.txt` |
| `tail` | Show last lines | `tail -n 20 file.txt` |
| `less` | View file (scrollable) | `less largefile.txt` |
| `more` | View file (page by page) | `more file.txt` |
| `nano` | Simple text editor | `nano file.txt` |
| `vi` / `vim` | Advanced text editor | `vim file.txt` |
| `echo` | Print text | `echo "Hello World"` |
| `wc` | Count lines/words/chars | `wc -l file.txt` |

### Nano Shortcuts

```
Ctrl+X  → Save and exit
Ctrl+O  → Save file
Ctrl+K  → Delete line
Ctrl+U  → Undo
```

### Vim Basics

```
i       → Insert mode
Esc     → Normal mode
:w      → Save
:q      → Quit
:wq     → Save and quit
dd      → Delete line
```

---

## File Permissions & Ownership

Control who can access and modify files.

| Command | Purpose | Example |
|---------|---------|---------|
| `chmod` | Change permissions | `chmod 755 file.txt` |
| `chown` | Change owner | `chown user:group file.txt` |
| `chgrp` | Change group | `chgrp groupname file.txt` |
| `ls -l` | View permissions | `ls -l file.txt` |
| `sudo` | Run as superuser | `sudo apt-get update` |
| `su` | Switch user | `su - username` |

### chmod Numbers

```
7 = read + write + execute (rwx)
6 = read + write (rw-)
5 = read + execute (r-x)
4 = read only (r--)
0 = no permissions (---)

chmod 755 file   → Owner: rwx, Others: r-x
chmod 644 file   → Owner: rw-, Others: r--
chmod 777 file   → Everyone: rwx
```

### Permission Format

```
-rw-r--r-- 1 user group 1024 May 6 10:30 file.txt
│││││││││  │ │    │     │    │
file type  links owner  group size
```

---

## Searching & Finding

Locate files and content quickly.

| Command | Purpose | Example |
|---------|---------|---------|
| `find` | Search files by name/type | `find . -name "*.txt"` |
| `grep` | Search text content | `grep "pattern" file.txt` |
| `grep -r` | Search recursively | `grep -r "text" /folder/` |
| `grep -i` | Case-insensitive search | `grep -i "TEXT" file.txt` |
| `locate` | Find file by name (fast) | `locate filename.txt` |
| `which` | Find command location | `which python3` |
| `whereis` | Find command & manual | `whereis ls` |

### find Examples

```bash
find . -type f -name "*.py"              # Find all Python files
find . -type d -name "folder"            # Find directories
find . -size +100M                       # Files larger than 100MB
find . -mtime -7                         # Modified in last 7 days
find . -type f -exec chmod 644 {} \;    # Change permissions recursively
```

### grep Examples

```bash
grep "error" log.txt                     # Find lines with "error"
grep -n "pattern" file.txt               # Show line numbers
grep -c "pattern" file.txt               # Count matches
grep -v "pattern" file.txt               # Show lines NOT matching
grep "^pattern" file.txt                 # Lines starting with pattern
```

---

## Text Processing

Manipulate and transform text.

| Command | Purpose | Example |
|---------|---------|---------|
| `cat` | Concatenate files | `cat file1.txt file2.txt` |
| `sort` | Sort lines | `sort file.txt` |
| `uniq` | Remove duplicates | `sort file.txt \| uniq` |
| `cut` | Extract columns | `cut -d',' -f1 file.csv` |
| `sed` | Stream editor | `sed 's/old/new/g' file.txt` |
| `awk` | Text processing | `awk '{print $1}' file.txt` |
| `tr` | Translate characters | `tr 'a-z' 'A-Z' < file.txt` |
| `paste` | Merge lines | `paste file1.txt file2.txt` |
| `diff` | Compare files | `diff file1.txt file2.txt` |

### Common sed Examples

```bash
sed 's/old/new/' file.txt                # Replace first occurrence per line
sed 's/old/new/g' file.txt               # Replace all occurrences
sed '5d' file.txt                        # Delete line 5
sed -n '1,10p' file.txt                  # Print lines 1-10
```

### awk Examples

```bash
awk '{print $1}' file.txt                # Print first column
awk -F',' '{print $2}' file.csv          # Print second column (CSV)
awk '{sum+=$1} END {print sum}' file.txt # Sum first column
awk 'NR>1' file.txt                      # Skip header row
```

---

## System Information

Check system status and configuration.

| Command | Purpose | Example |
|---------|---------|---------|
| `uname` | System info | `uname -a` |
| `uname -r` | Kernel version | `uname -r` |
| `lsb_release` | Ubuntu/Debian version | `lsb_release -a` |
| `whoami` | Current user | `whoami` |
| `hostname` | System hostname | `hostname` |
| `date` | Current date/time | `date` |
| `uptime` | System uptime | `uptime` |
| `df` | Disk space | `df -h` |
| `du` | Directory size | `du -sh /folder` |
| `free` | Memory usage | `free -h` |
| `top` | Process monitor | `top` |
| `htop` | Better process monitor | `htop` |

### System Information Examples

```bash
uname -a                    # All system information
lsb_release -a              # Ubuntu version details
cat /etc/os-release         # OS information
cat /proc/cpuinfo           # CPU details
cat /proc/meminfo           # Memory details
sensors                     # Temperature sensors
```

---

## Process Management

Monitor and control running processes.

| Command | Purpose | Example |
|---------|---------|---------|
| `ps` | List processes | `ps aux` |
| `ps aux \| grep` | Find specific process | `ps aux \| grep python` |
| `kill` | Terminate process | `kill PID` |
| `kill -9` | Force kill | `kill -9 PID` |
| `pkill` | Kill by name | `pkill python` |
| `bg` | Background process | `bg` |
| `fg` | Foreground process | `fg` |
| `jobs` | List background jobs | `jobs` |
| `nohup` | Run immune to hangup | `nohup script.sh &` |
| `&` | Run in background | `long_command &` |

### Process Examples

```bash
ps aux                      # List all processes
ps aux | grep python        # Find python processes
kill 1234                   # Kill process ID 1234
pkill -f "python script"    # Kill processes matching pattern
top                         # Real-time process monitor
htop                        # Interactive process monitor
```

---

## Networking

Connect to and manage networks.

| Command | Purpose | Example |
|---------|---------|---------|
| `ping` | Test connectivity | `ping google.com` |
| `ifconfig` | Network interfaces | `ifconfig` |
| `ip addr` | Show IP addresses | `ip addr show` |
| `netstat` | Network statistics | `netstat -tuln` |
| `ss` | Socket statistics | `ss -tuln` |
| `curl` | Download/test URLs | `curl https://example.com` |
| `wget` | Download files | `wget https://example.com/file.zip` |
| `ssh` | Secure shell | `ssh user@server.com` |
| `scp` | Secure copy | `scp file.txt user@server:/path/` |
| `ftp` / `sftp` | File transfer | `sftp user@server` |
| `nslookup` | DNS lookup | `nslookup google.com` |
| `whois` | Domain info | `whois example.com` |

### Networking Examples

```bash
ping -c 5 google.com        # Ping 5 times
ifconfig                    # All network interfaces
ip addr show                # All IP addresses
netstat -tuln               # All listening ports
ss -tuln                    # Socket listening ports
curl -I https://example.com # Check HTTP headers
wget -O filename.zip URL    # Download with custom name
ssh -i key.pem user@host    # SSH with key file
```

---

## Compression & Archives

Create and extract compressed files.

| Command | Purpose | Example |
|---------|---------|---------|
| `tar` | Archive files | `tar -czf archive.tar.gz folder/` |
| `tar -xzf` | Extract tar.gz | `tar -xzf archive.tar.gz` |
| `zip` | Create zip | `zip -r archive.zip folder/` |
| `unzip` | Extract zip | `unzip archive.zip` |
| `gzip` | Compress file | `gzip file.txt` |
| `gunzip` | Decompress file | `gunzip file.txt.gz` |
| `7z` | 7-Zip archive | `7z x archive.7z` |
| `bzip2` | Compress file | `bzip2 file.txt` |

---
**7z** and **7za** are both command-line tools related to the 7-Zip compression format, but they serve slightly different purposes:

## 7z

**7z is the main command-line utility** for the 7-Zip archive manager. It's a full-featured tool that can compress, decompress, and manage archives in multiple formats. With 7z, you can:

- Create and extract 7z archives (the native format)
- Work with other formats like ZIP, RAR, TAR, GZIP, and more
- Use advanced compression algorithms and settings
- Apply encryption and other advanced features

It's the standard tool you'd use for most compression tasks from the command line.

## 7za

**7za is a standalone executable** that's a smaller, simplified version of 7z. It's designed to be:

- **Portable and lightweight** — it can work independently without requiring installation or dependencies
- **Limited to fewer formats** — it primarily supports 7z, ZIP, and GZIP formats (not RAR or some other formats that full 7z supports)
- **Self-contained** — useful for scripting or systems where you need a minimal footprint

7za is often used in portable applications or scripts where you need compression functionality without the full 7-Zip suite.
## Extracting with 7za

The command to extract a .7z file using **7za** is:

```
7za x filename.7z
```

The `x` command extracts the archive while preserving the folder structure.

---

## Common 7za Extraction Commands

| Command | Purpose |
|---------|---------|
| `7za x filename.7z` | Extract with full folder structure |
| `7za x filename.7z -ooutput_directory` | Extract to a specific directory |
| `7za e filename.7z` | Extract all files to current directory (ignores folders) |
| `7za x filename.7z -pPassword` | Extract a password-protected archive |
| `7za l filename.7z` | List contents without extracting |

---

## Example

To extract `archive.7z` to a folder called `extracted`:

```
7za x archive.7z -oextracted
```

If you want to extract it to the current directory:

```
7za x archive.7z
```

---

In practical terms, if you're working on a system where 7-Zip is fully installed, you'd typically use **7z**. If you need a minimal, portable version or are distributing a tool that requires compression capabilities, **7za** is the better choice.

---

### tar Examples

```bash
tar -czf archive.tar.gz folder/         # Create compressed tar
tar -xzf archive.tar.gz                 # Extract tar.gz
tar -tzf archive.tar.gz                 # List contents
tar -cvzf archive.tar.gz file1 file2    # Create verbose
```

### Compression Formats

```bash
.tar           → tar cvf archive.tar folder/
.tar.gz        → tar czf archive.tar.gz folder/
.tar.bz2       → tar cjf archive.tar.bz2 folder/
.zip           → zip -r archive.zip folder/
.7z            → 7z a archive.7z folder/
```

---

## User & Group Management

Manage users and groups (requires sudo).

| Command | Purpose | Example |
|---------|---------|---------|
| `useradd` | Create user | `sudo useradd username` |
| `userdel` | Delete user | `sudo userdel username` |
| `usermod` | Modify user | `sudo usermod -aG groupname user` |
| `passwd` | Change password | `passwd` or `sudo passwd user` |
| `groupadd` | Create group | `sudo groupadd groupname` |
| `groupdel` | Delete group | `sudo groupdel groupname` |
| `id` | Show user/group info | `id` |
| `w` | Logged-in users | `w` |
| `who` | User login info | `who` |
| `sudo` | Run as superuser | `sudo command` |
| `visudo` | Edit sudo config | `sudo visudo` |

### User Management Examples

```bash
sudo useradd -m -s /bin/bash newuser    # Create user with home dir
sudo usermod -aG sudo newuser           # Add to sudo group
sudo usermod -aG groupname user         # Add user to group
sudo passwd newuser                     # Set password
id username                             # Show user info
groups username                         # Show user's groups
```

---

## Disk & Storage

Manage disks, partitions, and storage.

| Command | Purpose | Example |
|---------|---------|---------|
| `lsblk` | List block devices | `lsblk` |
| `blkid` | Block device IDs | `sudo blkid` |
| `df` | Disk free space | `df -h` |
| `du` | Directory usage | `du -sh /folder` |
| `mount` | Mount filesystem | `sudo mount /dev/sda1 /mnt` |
| `umount` | Unmount filesystem | `sudo umount /mnt` |
| `fdisk` | Partition editor | `sudo fdisk -l` |
| `parted` | Partition manager | `sudo parted /dev/sda` |
| `mkfs` | Create filesystem | `sudo mkfs.ext4 /dev/sda1` |

### Disk Examples

```bash
df -h                       # Disk space (human readable)
du -sh *                    # Size of all items in folder
du -sh /folder              # Total folder size
lsblk                       # List all disks
sudo fdisk -l               # List partitions
```

---

## Package Management

Install, update, and manage software.

### Debian/Ubuntu (apt)

| Command | Purpose | Example |
|---------|---------|---------|
| `apt update` | Update package list | `sudo apt update` |
| `apt upgrade` | Upgrade packages | `sudo apt upgrade` |
| `apt install` | Install package | `sudo apt install package-name` |
| `apt remove` | Remove package | `sudo apt remove package-name` |
| `apt search` | Search packages | `apt search package-name` |
| `apt show` | Package info | `apt show package-name` |
| `apt list --installed` | List installed | `apt list --installed` |

### apt Examples

```bash
sudo apt update              # Update package database
sudo apt upgrade             # Upgrade all packages
sudo apt install vim         # Install vim editor
sudo apt remove vim          # Remove vim
sudo apt autoremove          # Remove unused dependencies
apt search python            # Search for python packages
apt-cache depends package    # Show dependencies
```

### Other Package Managers

```bash
# Red Hat / CentOS / Fedora
sudo yum install package-name
sudo yum update
sudo yum remove package-name

# Arch Linux
sudo pacman -S package-name
sudo pacman -Syu             # Update all
sudo pacman -R package-name

# Alpine
apk add package-name
apk update
apk del package-name
```

---

## Useful Shortcuts & Tips

| Shortcut | Purpose |
|----------|---------|
| `Ctrl+C` | Cancel running command |
| `Ctrl+Z` | Suspend process |
| `Ctrl+D` | Exit terminal/logout |
| `Ctrl+L` | Clear screen |
| `Ctrl+A` | Go to line start |
| `Ctrl+E` | Go to line end |
| `Tab` | Auto-complete |
| `!!` | Repeat last command |
| `!$` | Last argument of previous command |
| `\|` | Pipe output to another command |
| `>` | Redirect output to file |
| `>>` | Append output to file |
| `<` | Read input from file |
| `&` | Run command in background |
| `;` | Run commands sequentially |
| `&&` | Run next command if previous succeeds |
| `\|\|` | Run next command if previous fails |

---

## Piping & Redirection

Chain commands together and manage input/output.

| Operator | Purpose | Example |
|----------|---------|---------|
| `\|` | Pipe output | `cat file.txt \| grep "pattern"` |
| `>` | Redirect to file (overwrite) | `echo "text" > file.txt` |
| `>>` | Append to file | `echo "text" >> file.txt` |
| `<` | Read from file | `command < file.txt` |
| `2>` | Redirect errors | `command 2> errors.txt` |
| `2>>` | Append errors | `command 2>> errors.txt` |
| `&>` | Redirect all output | `command &> output.txt` |
| `2>&1` | Redirect errors to stdout | `command 2>&1` |

### Piping Examples

```bash
cat file.txt | grep "error"              # Pipe grep to cat
ls -la | sort -k5 -n                     # Pipe to sort
cat log.txt | grep "error" | wc -l       # Multiple pipes
ps aux | grep python | grep -v grep      # Nested grep
```

### Redirection Examples

```bash
echo "Hello" > file.txt                  # Create/overwrite file
echo "World" >> file.txt                 # Append to file
command > output.txt 2>&1                # Capture all output
command > /dev/null 2>&1                 # Discard all output
cat < input.txt > output.txt             # Redirect input and output
```

---

## Wildcards & Pattern Matching

Use patterns to match multiple files.

| Pattern | Matches | Example |
|---------|---------|---------|
| `*` | Any characters | `*.txt` matches all text files |
| `?` | Single character | `file?.txt` matches file1.txt, fileA.txt |
| `[ ]` | Character range | `file[1-3].txt` matches file1.txt, file2.txt, file3.txt |
| `[!]` | Exclude characters | `file[!1].txt` matches anything except file1.txt |
| `{a,b}` | Multiple options | `file{1,2}.txt` matches file1.txt and file2.txt |

### Wildcard Examples

```bash
ls *.txt                     # All text files
cp file[1-3].txt /backup/    # Copy file1, file2, file3
rm file{old,backup}.txt      # Remove multiple files
find . -name "*.py" -type f  # Find all Python files
```

---

## Command History

Navigate and reuse previous commands.

| Command | Purpose | Example |
|---------|---------|---------|
| `history` | Show command history | `history` |
| `history 10` | Show last 10 commands | `history 10` |
| `history -c` | Clear history | `history -c` |
| `!5` | Run command #5 | `!5` |
| `!!` | Run last command | `!!` |
| `!command` | Run last matching command | `!grep` |
| `Ctrl+R` | Search history (reverse) | Press `Ctrl+R` then type |
| `history -w` | Save history to file | `history -w ~/.bash_history` |

### History Examples

```bash
history                      # Show all history
history 20                   # Show last 20 commands
!50                          # Run command 50
!ls                          # Run last ls command
Ctrl+R grep                  # Search for grep in history
```

---

## Useful Aliases & Functions

Create shortcuts for common commands.

### Add Aliases to ~/.bashrc

```bash
# Edit your bashrc
nano ~/.bashrc

# Add aliases
alias ll='ls -lah'
alias la='ls -A'
alias l='ls -CF'
alias c='clear'
alias home='cd ~'
alias update='sudo apt update && sudo apt upgrade'
alias server='ssh user@server.com'
alias copypath='readlink -f "$1" | xclip -selection clipboard'

# Reload bashrc
source ~/.bashrc
```

### Use Aliases

```bash
ll                           # Instead of ls -lah
update                       # Instead of sudo apt update && sudo apt upgrade
copypath file.txt            # Copy file path to clipboard
```

---

## Regular Expressions (Regex)

Pattern matching for grep, sed, awk.

| Pattern | Matches | Example |
|---------|---------|---------|
| `.` | Any single character | `gr.p` matches grep, grasp |
| `*` | Zero or more of previous | `ab*c` matches ac, abc, abbc |
| `+` | One or more of previous | `ab+c` matches abc, abbc (not ac) |
| `?` | Zero or one of previous | `ab?c` matches ac, abc |
| `^` | Start of line | `^error` matches lines starting with error |
| `$` | End of line | `success$` matches lines ending with success |
| `[ ]` | Character class | `[aeiou]` matches any vowel |
| `[^]` | Negated class | `[^0-9]` matches non-digits |
| `\|` | OR operator | `cat\|dog` matches cat or dog |
| `( )` | Group | `(ab)+` matches ab, abab, ababab |

### Regex Examples

```bash
grep "^error" log.txt        # Lines starting with error
grep "success$" log.txt      # Lines ending with success
grep "[0-9]" file.txt        # Lines with digits
grep "^[A-Z]" file.txt       # Lines starting with uppercase
sed 's/[0-9]//g' file.txt    # Remove all digits
```

---

## Variables & Environment

Work with shell variables.

| Command | Purpose | Example |
|---------|---------|---------|
| `echo $VAR` | Print variable value | `echo $PATH` |
| `export VAR=value` | Set environment variable | `export PATH=$PATH:/usr/bin` |
| `unset VAR` | Remove variable | `unset MYVAR` |
| `env` | Show all variables | `env` |
| `printenv` | Print environment | `printenv` |
| `$USER` | Current username | `echo $USER` |
| `$HOME` | Home directory | `cd $HOME` |
| `$PATH` | Executable paths | `echo $PATH` |
| `$PWD` | Current directory | `echo $PWD` |
| `$?` | Last exit status | `echo $?` |

### Variable Examples

```bash
export MYVAR="Hello World"   # Set variable
echo $MYVAR                  # Use variable
PATH=$PATH:/new/path         # Add to PATH
VAR=value command            # Set for single command
unset MYVAR                  # Remove variable
```

---

## Scripting Basics

Write simple bash scripts.

### Create a Script

```bash
#!/bin/bash

# This is a comment

# Variables
name="John"
age=30

# Echo output
echo "Hello, $name!"
echo "Age: $age"

# Conditionals
if [ $age -gt 18 ]; then
    echo "Adult"
else
    echo "Minor"
fi

# For loop
for i in {1..5}; do
    echo "Number: $i"
done

# While loop
count=1
while [ $count -le 3 ]; do
    echo "Count: $count"
    count=$((count + 1))
done
```

### Save and Run

```bash
nano script.sh               # Create script
chmod +x script.sh           # Make executable
./script.sh                  # Run script
bash script.sh               # Run with bash
```

### Conditional Operators

```bash
-eq     → Equal
-ne     → Not equal
-lt     → Less than
-gt     → Greater than
-le     → Less than or equal
-ge     → Greater than or equal

-z      → String is empty
-n      → String is not empty
-f      → File exists
-d      → Directory exists
```

---

## One-Liners & Quick Tips

Practical command combinations.

```bash
# Find and delete files
find . -name "*.tmp" -delete

# Find largest files
find . -type f -exec ls -lh {} \; | sort -k5 -hr | head -10

# Count lines in all files
find . -name "*.txt" -exec wc -l {} + | tail -1

# Backup directory
tar -czf backup_$(date +%Y%m%d).tar.gz /path/to/folder

# Find and replace in multiple files
find . -name "*.txt" -exec sed -i 's/old/new/g' {} \;

# Monitor file changes
watch -n 1 'ls -lh file.txt'

# Show system load
watch -n 1 'free -h && uptime'

# List files by size
ls -lhS

# Show top 10 largest folders
du -sh */ | sort -rh | head -10

# Kill all processes matching pattern
pkill -f "python script.py"

# Count files by type
find . -type f | sed 's/.*\.//' | sort | uniq -c

# Create multiple directories
mkdir -p dir1/{sub1,sub2,sub3}

# Extract multiple archives
for file in *.tar.gz; do tar -xzf "$file"; done

# Compress multiple files
tar -czf archive.tar.gz file1 file2 file3

# Rename batch files
for file in *.old; do mv "$file" "${file%.old}.new"; done

# Show disk usage by folder
du -sh * | sort -hr

# Monitor command output changes
watch -d 'ps aux | grep python'

# Quick HTTP server
python3 -m http.server 8000

# Check open ports
sudo netstat -tulpn | grep LISTEN

# Count processes by user
ps aux | awk '{print $1}' | sort | uniq -c

# Show network connections
netstat -an | grep ESTABLISHED | wc -l
```

---

## Helpful Resources

### Get Help

```bash
man command              # Full manual
command --help          # Quick help
command -h              # Short help
whatis command          # One-line description
info command            # Detailed info
```

### Common Directories

```
/home              → User home directories
/root              → Root user home
/bin               → Essential user commands
/sbin              → Essential system commands
/usr/bin           → User programs
/usr/local/bin     → Local programs
/etc               → Configuration files
/var               → Variable data
/tmp               → Temporary files
/opt               → Optional software
/dev               → Device files
```

---
