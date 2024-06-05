Here's the cheat sheet for the commands from the provided Linux Fundamentals Module, formatted in markdown:

## Linux Fundamentals Cheat Sheet

### Basic Commands

| Command | Description |
|---------|-------------|
| `man <tool>` | Opens man pages for the specified tool. |
| `<tool> -h` | Prints the help page of the tool. |
| `apropos <keyword>` | Searches through man pages' descriptions for instances of a given keyword. |
| `cat` | Concatenate and print files. |
| `whoami` | Displays current username. |
| `id` | Returns user's identity. |
| `hostname` | Sets or prints the name of the current host system. |
| `uname` | Prints operating system name. |
| `pwd` | Returns working directory name. |

### Network Commands

| Command | Description |
|---------|-------------|
| `ifconfig` | Used to assign or view an address to a network interface and/or configure network interface parameters. |
| `ip` | Utility to show or manipulate routing, network devices, interfaces, and tunnels. |
| `netstat` | Shows network status. |
| `ss` | Another utility to investigate sockets. |

### Process Commands

| Command | Description |
|---------|-------------|
| `ps` | Shows process status. |
| `who` | Displays who is logged in. |
| `env` | Prints environment or sets and executes a command. |

### Device Commands

| Command | Description |
|---------|-------------|
| `lsblk` | Lists block devices. |
| `lsusb` | Lists USB devices. |
| `lsof` | Lists opened files. |
| `lspci` | Lists PCI devices. |

### User Management

| Command | Description |
|---------|-------------|
| `sudo` | Execute command as a different user. |
| `su` | Switches to another user ID (default is superuser). |
| `useradd` | Creates a new user or updates default new user information. |
| `userdel` | Deletes a user account and related files. |
| `usermod` | Modifies a user account. |
| `addgroup` | Adds a group to the system. |
| `delgroup` | Removes a group from the system. |
| `passwd` | Changes user password. |

### Package Management

| Command | Description |
|---------|-------------|
| `dpkg` | Install, remove and configure Debian-based packages. |
| `apt` | High-level package management command-line utility. |
| `aptitude` | Alternative to apt. |
| `snap` | Install, remove and configure snap packages. |
| `gem` | Standard package manager for Ruby. |
| `pip` | Standard package manager for Python. |
| `git` | Revision control system command-line utility. |

### System Management

| Command | Description |
|---------|-------------|
| `systemctl` | Command-line based service and systemd control manager. |
| `ps` | Prints a snapshot of the current processes. |
| `journalctl` | Query the systemd journal. |
| `kill` | Sends a signal to a process. |
| `bg` | Puts a process into the background. |
| `jobs` | Lists all processes that are running in the background. |
| `fg` | Puts a process into the foreground. |

### Networking

| Command | Description |
|---------|-------------|
| `curl` | Command-line utility to transfer data from or to a server. |
| `wget` | An alternative to curl that downloads files from FTP or HTTP(s) server. |
| `python3 -m http.server` | Starts a Python3 web server on TCP port 8000. |

### File Operations

| Command | Description |
|---------|-------------|
| `ls` | Lists directory contents. |
| `cd` | Changes the directory. |
| `clear` | Clears the terminal. |
| `touch` | Creates an empty file. |
| `mkdir` | Creates a directory. |
| `tree` | Lists the contents of a directory recursively. |
| `mv` | Move or rename files or directories. |
| `cp` | Copy files or directories. |
| `nano` | Terminal based text editor. |
| `which` | Returns the path to a file or link. |
| `find` | Searches for files in a directory hierarchy. |
| `updatedb` | Updates the locale database for existing contents on the system. |
| `locate` | Uses the locale database to find contents on the system. |
| `more` | Pager that is used to read STDOUT or files. |
| `less` | An alternative to more with more features. |
| `head` | Prints the first ten lines of STDOUT or a file. |
| `tail` | Prints the last ten lines of STDOUT or a file. |
| `sort` | Sorts the contents of STDOUT or a file. |
| `grep` | Searches for specific results that contain given patterns. |
| `cut` | Removes sections from each line of files. |
| `tr` | Replaces certain characters. |
| `column` | Command-line based utility that formats its input into multiple columns. |
| `awk` | Pattern scanning and processing language. |
| `sed` | A stream editor for filtering and transforming text. |
| `wc` | Prints newline, word, and byte counts for a given input. |

### File Permissions

| Command | Description |
|---------|-------------|
| `chmod` | Changes permission of a file or directory. |
| `chown` | Changes the owner and group of a file or directory. |
