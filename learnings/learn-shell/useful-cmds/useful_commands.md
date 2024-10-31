# Shell Command Basics

## Table of Content

- [About](#about)
- [Contents](#contents)
  - [File Inspection and Analysis](#file-inspection-and-analysis)
  - [File and Directory Management](#file-and-directory-management)
  - [File Viewing and Manipulation](#file-viewing-and-manipulation)
  - [System Information](#system-information)
  - [Networking](#networking)
  - [Process Management](#process-management)
  - [Compression and Archiving](#compression-and-archiving)
  - [Text Processing](#text-processing)
  - [User and Permission Management](#user-and-permission-management)
  - [Miscellaneous](#miscellaneous)

## About

This file contains notes about some useful basic shell commands that can be used.

## Contents

### File Inspection and Analysis

- **nm** | List symbols from object files  
  - **Syntax**: `nm [options] object_file`
  - **Flags**:
    - `-g`: Show only external (global) symbols.
    - `-A`: Show filenames for each symbol.
    - `-s`: Print sorted symbols by address.
  - **Example**: `nm -g myfile.o`

- **objdump** | Display information from object files  
  - **Syntax**: `objdump [options] object_file`
  - **Flags**:
    - `-d`: Disassemble code sections.
    - `-f`: Show file headers.
    - `-s`: Display full contents of all sections.
  - **Example**: `objdump -d myfile.o`

- **readelf** | Display information about ELF files  
  - **Syntax**: `readelf [options] elf_file`
  - **Flags**:
    - `-h`: Show ELF header.
    - `-S`: Display section headers.
    - `-l`: Show program headers.
  - **Example**: `readelf -h myfile`

### File and Directory Management

- **ls** | List directory contents  
  - **Syntax**: `ls [options] [directory]`
  - **Flags**:
    - `-a`: Show all files, including hidden ones.
    - `-l`: Use a long listing format.
    - `-h`: Display file sizes in human-readable format.
  - **Example**: `ls -lh`

- **cd** | Change the current directory  
  - **Syntax**: `cd [directory]`
  - **Example**: `cd /path/to/directory`

- **mkdir** | Make a new directory  
  - **Syntax**: `mkdir [options] directory_name`
  - **Flags**:
    - `-p`: Create parent directories as needed.
    - `-v`: Show each directory created.
  - **Example**: `mkdir -pv new_folder/sub_folder`

- **rm** | Remove files or directories  
  - **Syntax**: `rm [options] file_or_directory`
  - **Flags**:
    - `-r`: Recursively remove directories.
    - `-f`: Force removal without confirmation.
    - `-i`: Prompt before each file removal.
  - **Example**: `rm -rf folder_name`

- **cp** | Copy files or directories  
  - **Syntax**: `cp [options] source destination`
  - **Flags**:
    - `-r`: Copy directories recursively.
    - `-u`: Only copy files that are newer than the destination.
    - `-v`: Verbose output, showing files as they are copied.
  - **Example**: `cp -ru source_dir destination_dir`

- **mv** | Move or rename files or directories  
  - **Syntax**: `mv [options] source destination`
  - **Flags**:
    - `-i`: Prompt before overwriting.
    - `-u`: Only move files if the source is newer.
    - `-v`: Verbose output, showing files as they are moved.
  - **Example**: `mv -u old_name new_name`

- **touch** | Create an empty file / change file timestamps  
  - **Syntax**: `touch [options] file`
  - **Flags**:
    - `-a`: Change only access time.
    - `-m`: Change only modification time.
    - `-t`: Specify a timestamp.
  - **Example**: `touch -a -m newfile.txt`

- **find** | Search for files and directories  
  - **Syntax**: `find [starting_dir] [options] [expression]`
  - **Flags**:
    - `-name`: Search by name.
    - `-type`: Search by type (e.g., `f` for file, `d` for directory).
    - `-exec`: Execute command on matching files.
  - **Example**: `find . -name "*.txt" -exec rm {} \;`

### File Viewing and Manipulation

- **cat** | Concatenate and display file content  
  - **Syntax**: `cat [options] [file]`
  - **Flags**:
    - `-n`: Number all output lines.
    - `-s`: Suppress repeated empty output lines.
  - **Example**: `cat -n file.txt`

- **less / more** | View file content one screen at a time  
  - **Syntax**: `less [file]` or `more [file]`
  - **Flags**:
    - `-N`: Show line numbers.
    - `-S`: Truncate long lines instead of wrapping.
  - **Example**: `less -N largefile.txt`

- **head / tail** | Display the beginning or end of a file  
  - **Syntax**: `head [options] [file]` or `tail [options] [file]`
  - **Flags**:
    - `-n [N]`: Display first/last `N` lines.
    - `-c [N]`: Display first/last `N` bytes.
  - **Example**: `head -n 5 file.txt`

- **grep** | Search for patterns in files  
  - **Syntax**: `grep [options] pattern [file]`
  - **Flags**:
    - `-i`: Case-insensitive search.
    - `-r`: Search recursively in directories.
    - `-n`: Show line numbers with output.
  - **Example**: `grep -ri "error" .`

- **wc** | Count lines, words, and characters in files  
  - **Syntax**: `wc [options] [file]`
  - **Flags**:
    - `-l`: Count lines.
    - `-w`: Count words.
    - `-c`: Count bytes.
  - **Example**: `wc -l file.txt`

- **sort** | Sort lines of text files  
  - **Syntax**: `sort [options] [file]`
  - **Flags**:
    - `-r`: Sort in reverse order.
    - `-u`: Remove duplicate lines.
    - `-n`: Sort numerically.
  - **Example**: `sort -nr file.txt`

- **uniq** | Report or omit repeated lines  
  - **Syntax**: `uniq [options] [file]`
  - **Flags**:
    - `-c`: Count occurrences of each line.
    - `-d`: Only show duplicate lines.
    - `-u`: Only show unique lines.
  - **Example**: `sort file.txt | uniq -c`

### System Information

- **pwd** | Print the current working directory  
  - **Syntax**: `pwd`
  - **Flags**:
    - `-P`: Show physical directory without symbolic links.
  - **Example**: `pwd -P`

- **whoami** | Display the current user  
  - **Syntax**: `whoami`
  - **Example**: `whoami`

- **uname** | Print system information  
  - **Syntax**: `uname [options]`
  - **Flags**:
    - `-a`: All system information.
    - `-s`: Kernel name.
    - `-r`: Kernel release.
  - **Example**: `uname -a`

- **df** | Display disk space usage  
  - **Syntax**: `df [options] [file_system]`
  - **Flags**:
    - `-h`: Human-readable sizes.
    - `-T`: Show file system type.
  - **Example**: `df -hT`

- **du** | Estimate file and directory space usage  
  - **Syntax**: `du [options] [file_or_directory]`
  - **Flags**:
    - `-h`: Human-readable format.
    - `-s`: Show only the total for each argument.
  - **Example**: `du -sh folder_name`

- **htop** | Display system tasks and memory usage  
  - **Syntax**: `htop`
  - **Example**: `htop`.

- **ps** | Report a snapshot of current processes  
  - **Syntax**: `ps [options]`
  - **Example**: `ps aux` – displays all running processes in detail.

### Networking

- **ping** | Check network connectivity  
  - **Syntax**: `ping [options] hostname_or_ip`
  - **Flags**:
    - `-c [N]`: Send `N` packets.
    - `-i [interval]`: Set time interval between packets.
  - **Example**: `ping -c 4 google.com`

- **ifconfig / ip** | Configure network interfaces  
  - **Syntax**: `ifconfig [interface] [options]` or `ip [options]`
  - **Flags**:
    - `up/down`: Activate/deactivate interface.
    - `ip addr show`: Display IP addresses.
  - **Example**: `ifconfig eth0 up`

- **ssh** | Securely connect to a remote machine  
  - **Syntax**: `ssh [options] user@host`
  - **Flags**:
    - `-i [identity_file]`: Use specific key for authentication.
    - `-p [port]`: Specify port.
  - **Example**: `ssh -i ~/.ssh/id_rsa -p 2222 user@host`

- **scp** | Securely copy files between hosts  
  - **Syntax**: `scp [options] source destination`
  - **Flags**:
    - `-r`: Recursively copy directories.
    - `-P [port]`: Specify port.
  - **Example**: `scp -P 2222 file.txt user@host:/path`

- **wget / curl** | Download files from the web  
  - **Syntax**: `wget [options] URL` or `curl [options] URL`
  - **Flags for wget**:
    - `-O [file]`: Save output to a specified file.
    - `-q`: Quiet mode (no output).
    - `--limit-rate=[rate]`: Limit download speed.
  - **Flags for curl**:
    - `-o [file]`: Save output to a specified file.
    - `-L`: Follow redirects.
    - `-s`: Silent mode (no progress or error messages).
  - **Example**: `wget https://example.com/file.zip` or `curl -O https://example.com/file.zip`

### Process Management

- **kill** | Terminate processes by PID  
  - **Syntax**: `kill [options] PID`
  - **Flags**:
    - `-l`: List all signal names.
    - `-s [signal]`: Specify a signal to send.
  - **Example**: `kill -9 1234`

- **killall** | Terminate processes by name  
  - **Syntax**: `killall [options] process_name`
  - **Flags**:
    - `-u [user]`: Kill processes for a specific user.
    - `-r`: Use regular expressions for process names.
  - **Example**: `killall -u username firefox`

- **bg / fg** | Move jobs to the background or foreground  
  - **Syntax**: `bg [job_spec]` or `fg [job_spec]`
  - **Example**: `bg %1` or `fg %1`

- **jobs** | List active jobs  
  - **Syntax**: `jobs [options]`
  - **Example**: `jobs -l`

### Compression and Archiving

- **tar** | Archive files  
  - **Syntax**: `tar [options] archive_name files`
  - **Flags**:
    - `-c`: Create a new archive.
    - `-x`: Extract files from an archive.
    - `-v`: Verbose mode (show progress).
    - `-f`: Specify the archive file name.
  - **Example**: `tar -czvf archive.tar.gz folder_name`

- **gzip / gunzip** | Compress or decompress files  
  - **Syntax**: `gzip [file]` or `gunzip [file]`
  - **Flags**:
    - `-k`: Keep original file.
    - `-v`: Verbose mode.
  - **Example**: `gzip file.txt`

- **zip / unzip** | Create or extract ZIP files  
  - **Syntax**: `zip [options] archive file` or `unzip [archive]`
  - **Flags for zip**:
    - `-r`: Recursively add files and directories.
    - `-e`: Encrypt the zip file.
  - **Flags for unzip**:
    - `-l`: List contents of the zip file.
    - `-d [directory]`: Extract to a specified directory.
  - **Example**: `zip -r archive.zip folder_name` or `unzip archive.zip`

### Text Processing

- **awk** | Pattern scanning and processing language  
  - **Syntax**: `awk 'pattern {action}' file`
  - **Example**: `awk '{print $1}' file.txt`

- **sed** | Stream editor for filtering and transforming text  
  - **Syntax**: `sed [options] 'command' file`
  - **Flags**:
    - `-i`: Edit files in place.
    - `-e`: Add commands to the script.
  - **Example**: `sed -i 's/old/new/g' file.txt`

- **cut** | Remove sections from each line of files  
  - **Syntax**: `cut [options] file`
  - **Flags**:
    - `-d [delimiter]`: Specify a delimiter.
    - `-f [fields]`: Select specific fields.
  - **Example**: `cut -d',' -f1 file.csv`

- **tr** | Translate or delete characters  
  - **Syntax**: `tr [options] set1 [set2]`
  - **Flags**:
    - `-d [set]`: Delete characters in set.
    - `-s`: Squeeze repeated characters.
  - **Example**: `echo "abc" | tr 'a-z' 'A-Z'`

### User and Permission Management

- **chmod** | Change file permissions  
  - **Syntax**: `chmod [options] mode file`
  - **Flags**:
    - `-R`: Change permissions recursively.
    - `-v`: Verbose output.
  - **Example**: `chmod -R 755 folder`

- **chown** | Change file owner and group  
  - **Syntax**: `chown [options] owner:group file`
  - **Flags**:
    - `-R`: Change ownership recursively.
    - `-v`: Verbose output.
  - **Example**: `chown -R user:group file.txt`

- **sudo** | Execute a command as another user  
  - **Syntax**: `sudo [command]`
  - **Flags**:
    - `-u [user]`: Run the command as the specified user.
    - `-k`: Invalidate the user's cached credentials.
  - **Example**: `sudo -u anotheruser apt update`

### Miscellaneous

- **alias** | Create shortcuts for commands  
  - **Syntax**: `alias name='command'`
  - **Example**: `alias ll='ls -la'`

- **history** | Show command history  
  - **Syntax**: `history [options]`
  - **Flags**:
    - `-c`: Clear the history list.
    - `-w`: Write the current history to the history file.
  - **Example**: `history | grep "search_term"`

- **date** | Display or set the system date and time  
  - **Syntax**: `date [options]`
  - **Flags**:
    - `-u`: Display time in UTC.
    - `-d [string]`: Display time described by the string.
  - **Example**: `date "+%Y-%m-%d %H:%M:%S"`

- **echo** | Display a line of text  
  - **Syntax**: `echo [options] [string]`
  - **Flags**:
    - `-n`: Do not output the trailing newline.
    - `-e`: Enable interpretation of backslash escapes.
  - **Example**: `echo -e "Hello,\nWorld!"`

- **man** | Display the user manual for commands  
  - **Syntax**: `man [command]`
  - **Example**: `man ls`
  