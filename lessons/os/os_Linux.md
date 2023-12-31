-------------------------------------------------------------------------------
# Google IT support — Operating Systems (Linux)

<!-- MarkdownTOC -->

- [1. Navigating the system](#1-navigating-the-system)
    - [1.1. Basics](#11-basics)
    - [1.2. Terminal commands](#12-terminal-commands)
    - [1.3. File and text manipulation](#13-file-and-text-manipulation)
    - [1.4. I/O streams and the pipeline](#14-io-streams-and-the-pipeline)
- [2. Users and permissions](#2-users-and-permissions)
    - [2.1. Users and groups](#21-users-and-groups)
    - [2.2. Permissions](#22-permissions)
    - [2.3. Special permissions](#23-special-permissions)
- [3. Package and software management](#3-package-and-software-management)
    - [3.1. Software packages](#31-software-packages)
    - [3.2. Package managers](#32-package-managers)
    - [3.3. Archives](#33-archives)
    - [3.4. Mobile app packages](#34-mobile-app-packages)
    - [3.5. Devices and drivers](#35-devices-and-drivers)
    - [3.6. OS updates](#36-os-updates)
- [4. File systems](#4-file-systems)
    - [4.1. Review of file systems](#41-review-of-file-systems)
    - [4.2. Partitions](#42-partitions)
    - [4.3. Disk partitioning, formatting and mounting](#43-disk-partitioning-formatting-and-mounting)
    - [4.4. Virtual memory](#44-virtual-memory)
    - [4.5. Files and metadata](#45-files-and-metadata)
    - [4.6. Disk usage](#46-disk-usage)
    - [4.7. File system repair](#47-file-system-repair)
- [5. Process management](#5-process-management)
    - [5.1. Processes](#51-processes)
    - [5.2. Process monitoring](#52-process-monitoring)
    - [5.3. Process management](#53-process-management)
    - [5.4. Jobs](#54-jobs)
    - [5.5. Resource monitoring](#55-resource-monitoring)
- [6. Operating systems in practice](#6-operating-systems-in-practice)
    - [6.1. Remote connection](#61-remote-connection)
    - [6.2. Logs](#62-logs)
    - [6.3. OS deployment](#63-os-deployment)
    - [6.4. Networking](#64-networking)
    - [6.5. Aliases](#65-aliases)
    - [6.6. Environment variables](#66-environment-variables)

<!-- /MarkdownTOC -->

-------------------------------------------------------------------------------

## Content

[Contents](../README.md#contents)


## 1. Navigating the system

To navigate files and directories in operating systems you can use GUI or *command-line interface* (through *shell*). These files and directories are organized in a hierarchical directory tree (main directory branches off and holds other directories and files).

### 1.1. Basics

- the path to the *root directory* (the parent for all other directories) is denoted by `/`
- *root directory* contains:
    ```
    /bin  : essential binaries and programs
    /etc  : system configuration files
    /home : users files and directories
    /opt  : package-manager installed files
    /proc : information about currently running processes
    /root : administrator account files and directories
    /sbin : important system binaries and programs
    /tmp  : temporary files
    /usr  : user installed software
    /var  : system logs
    ```
- subdirectories are separated by `/` (forward slash)
- hidden files and directories start with a `.` (e.g., `.hidden_file`)
- most common *command-line interface* is **bash** ([reference manual](https://www.gnu.org/software/bash/manual/bash.html))
- strings in *bash* can be denoted by `'my file'` or by `my\ file` (`\` is the escape character)
- *tab completion* and *wildcards* are available in *bash*


### 1.2. Terminal commands

```console
<user>@<computer>:<path>$ <command> <options> <arguments>
```

```
man <command>            : show manual for command (or info <command>)
<command> --help         : show available flags for command
echo <str>               : print input
clear                    : clear screen (or ctrl + L)
history                  : show command history (or ctrl + R for search)
reset                    : reinitialize terminal
exit                     : close terminal
reboot                   : reboot computer
shutdown                 : shutdown computer

pwd                      : print working directory
ls <path>                : list files and directories (-l list, -a all, -h human readable, -d directories)
tree <path>              : list files and directories in a tree-like format
cd <path>                : change directory
touch <path1> ...        : create files (file{1..5}.txt for similar names)
mkdir <path1> ...        : create directories (dir{1..5} for similar names)
rm <path1> ...           : remove files/directories (-r for directories, -f force)
cp <path1> <path2>       : copy file/directory (-r for directory)
mv <path1> <path2>       : move (or rename) file/directory
mc                       : Midnight Commander file manager
```

**System info**:
```
uname -a                 : OS info (or lsb_release -a)
lscpu                    : CPU info
free -h                  : RAM info
ip addr                  : network info
df -h                    : storage info (du -cksh for folders, --max-depth 1)
```

**Wildcards** (symbols used to represent one or more characters):
```
~                        : /home/user
/                        : / (i.e., root directory)
..                       : one level up
.                        : current directory
-                        : back
?                        : any symbol
*                        : any number of any symbols
```

**Terminal shortcuts**:

| shortcut                                                     | description                                     |
| ------------------------------------------------------------ | ----------------------------------------------- |
| <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>C</kbd> / <kbd>V</kbd> | copy/paste                                      |
| <kbd>Ctrl</kbd> + <kbd>A</kbd> / <kbd>E</kbd>                | move cursor to the begining/end of line         |
| <kbd>Ctrl</kbd> + <kbd>W</kbd>                               | delete a word to the left                       |
| <kbd>Ctrl</kbd> + <kbd>U</kbd> / <kbd>K</kbd>                | delete everything to the left/right of a cursor |
| <kbd>Alt</kbd> + <kbd>B</kbd> / <kbd>F</kbd>                 | move one word back/forward                      |
| <kbd>Tab</kbd>                                               | tab completion                                  |
|                                                              |                                                 |
| <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>T</kbd>            | open new terminal tab                           |
| <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>W</kbd>            | close current terminal tab                      |
| <kbd>Alt</kbd> + <kbd><#></kbd>                              | swith to <#>th terminal tab                     |
| <kbd>Ctrl</kbd> + <kbd>L</kbd>                               | clear terminal screen                           |
| <kbd>Ctrl</kbd> + <kbd>C</kbd>                               | kill current process                            |
| <kbd>Ctrl</kbd> + <kbd>Z</kbd>                               | suspend current process                         |

To make command history be based on relevancy (instead of chronological order) add to `~/.inputrc` the following:
```
"\e[A": history-search-backward
"\e[B": history-search-forward
"\e[C": forward-char
"\e[D": backward-char
```


### 1.3. File and text manipulation

```
<program> <file>         : execute file (or ./<file>)
sh <file>                : execute shell file

cat <file>               : view contents of a file
head/tail <file>         : view first/last 10 lines of a file
less <file>              : open file with less text editor
nano <file>              : open file with nano text editor

find <path> -name <file> : search for a file
grep <str> <files>       : search within files (can use regexes)
wc <opt> <path>          : count <opt> in a file (-l lines, -w words, -c characters)
diff <path1> <path2>     : compare files/directories
```


### 1.4. I/O streams and the pipeline

- there are three main I/O streams: **stdin** (files/keyboard), **stdout** (terminal by default) and **stderr** (terminal by default)
- the direction of these streams can be changed with *redirector operators*
- there is a special file that discards all the data written to it (`/dev/null`)

<p style="text-align:center;"><img src="data/shell IO streams.png" width="500" title="Shell I/O streams"></p>

<!-- graph LR
  id1(Standard Input)
  id2[Shell]
  id3(Standard Output)
  id4(Standard Error)

  id1 -- #0 --\> id2
  id2 -- #1 --\> id3
  id2 -- #2 --\> id4 -->

```
<com>  <   <file>        : stdin from file
<com>  >   <file>        : stdout to file (rewrite)
<com>  >>  <file>        : stdout to file (append)
<com>  2>  <file>        : stderr to file (rewrite)
<com>  2>> <file>        : stderr to file (append)
<com1> | <com2>          : pipeline (stdin[i+1] = stdout[i])
```

[Content](#content)
-------------------------------------------------------------------------------
## 2. Users and permissions

### 2.1. Users and groups

- there are two different types of users: *standard users* (have restricted access) and *administrators* (have complete control of a machine, i.e., can grant access for other users, install software, change restricted system settings, etc.)
- there is also a special user, that is automatically created after OS installation called **root user**; they have all the OS privileges (i.e., they are the *super user*)
- good practice: not to be logged in as *root* all the time, but use your own account, and acquire *root privileges* only when you need them
- users are put together in *groups* according to their levels of access and permissions
- good password practice: administrator sets a default password for a user, and then makes them change it on the next log in

```
sudo <command>           : run command as root
sudo su -                : substitute user to root (exit: to log out)
users                    : show currently logged in users
groups <user>            : show user groups

useradd <user>           : add new user
userdel <user>           : delete user (-r with their home directory)
passwd  <user>           : change user password
passwd -e <user>         : expire user password (to force user change it on the next log in)

```

- Groups membership information is stored in `/etc/group`. Each line represents a group and has four fields separated by colons: group name, group password (defaults to the root password, usually encrypted and stored in a separate file), group ID, and list of users in the group.
- Users information is stored in `/etc/passwd` (most users in Linux are just running processes associated with a user). Each line represents a user; first three fields: username, password (encrypted and stored in a separate file), and UID (user ID, e.g., for root `UID=0`). Users with `UID < 1000` are system processes, and users with `UID > 1000` are real.
- Passwords are securely scrambled and stored in `etc/shadow`, which can only be read by root.


### 2.2. Permissions

There are three different types of permissions: *read*, *write* and *execute*. To view files/directories permissions use `ls -l`:

```console
user@linux:~$ ls -l
total 10K
drwxrwxr-x <N> <user> <group> <size> <date> <name>
```

```
d/l/-   : directory/link/file
rwx/--- : read/write/execute for user/group/all other users
N       : number of hardlinks or directories inside this directory
user    : owner of a file/directory
group   : owner group
size    : size of a file/directory
date    : last modified
name    : name of a file/directory
```

```
chmod ### <path>         : change file/directory permissions, where ### are
                           1) 3 symbols: [ugoa][+-=][rwx]
                              ugoa (user, group, other, all)
                              +-=  (add, remove, assign)
                              rwx  (read, write, execute)
                           2) 3 numbers: 4 - read, 2 - write, 1 - execute
                              (add these numbers to set permissions)
chown <user>  <path>     : change the owner of a file/directory
chgrp <group> <path>     : change the group file/directory belongs to

Examples:
u+x       (execute for the owner)
ug=rw,o=r (read and write for the owner and their group, read for other users)
a-x       (remove execute for all users)
g=u       (set group permissions as owner permissions)
754       (rwxr-xr--)
```

| Base-8  | Base-2  |  Permissions  |
|:-------:|:-------:|:-------------:|
|    0    |   000   |     `---`     |
|    1    |   001   |     `--x`     |
|    2    |   010   |     `-w-`     |
|    3    |   011   |     `-wx`     |
|    4    |   100   |     `r--`     |
|    5    |   101   |     `r-x`     |
|    6    |   110   |     `rw-`     |
|    7    |   111   |     `rwx`     |


### 2.3. Special permissions

Sometimes you want to allow users do actions that require *root privileges* without giving them root access (e.g., to change user password you need to write into `etc/shadow` which is owned by root). For this reason *special permissions* exist:

1. **setuid**
    - allows to run files by the permission of the owner
    - file with a *setuid* flag has an `s` instead of `x` in its list of owner permissions

2. **setgid**
    - allows to run files as a member of the file group
    - file with a *setgid* flag has an `s` instead of `x` in its list of group permissions

3. **sticky bit**
    - allows anyone to write to a file/directory, but only the owner or root can delete anything
    - file/directory with a *sticky bit* flag has a `t` instead of `x` in its list of permissions for other users
    - often used for temporary files

```
sudo chmod u+s <path>    : set setuid flag for a file (or 4###)
sudo chmod g+s <path>    : set setgid flag for a file (or 2###)
sudo chmod +t  <path>    : set sticky bit flag for a file/directory (or 1###)
```

[Content](#content)
-------------------------------------------------------------------------------
## 3. Package and software management

### 3.1. Software packages

Developers package software using *software compiling tools*. Different Linux distributions can use different methods for software packaging, e.g., Red Hat uses `.rpm` (Red Hat package manager) packages and Ubuntu uses `.deb` (Debian) packages. They contain instructions for a computer to perform, computer code and other files that program might use.

```
sudo dpkg -i <name.deb>  : install debian package
sudo dpkg -r <name>      : remove debian package
dpkg -l                  : list installed debian packages
```

Packages usually rely on other pieces of code in order to work. In Linux these dependencies can be other packages or shared libraries. Standalone packages (e.g., `.deb` packages) don't install neccesary dependencies automatically, that's why *package managers* exist.


### 3.2. Package managers

A *package manager* makes sure that the process of software installation, removal, update, and dependency management is as easy and automatic as possible. APT (*advanced package tool*) is a default package manager for Ubuntu.

- in Ubuntu the link to a package repository is stored in `/etc/apt/sources.list`
- there are also special repositories called [PPAs](https://help.launchpad.net/Packaging/PPA) (*personal package archives*), which are hosted on Launchpad servers (owned by Canonical Limited) and used by open source developers

```
sudo apt install <name>  : install package (with dependencies)
sudo apt remove  <name>  : remove package (with dependencies)
sudo apt purge   <name>  : remove package and its config files (with dependencies)
sudo apt autoremove      : remove unnecessary packages

sudo apt update          : update the list of packages for upgrade
sudo apt upgrade         : upgrade installed packages
```


### 3.3. Archives

**Archive** is one or more files compressed into a single file.

- popular archive types: `.tar`, `.zip`, and `.rar`.
- archives can be used for software packaging (*installing from source*).
- popular tools for working with archives: [tar](http://www.linfo.org/tar.html) and P7zip

```
zip   <path> ...         : create .zip archive (-r directory, -e encrypt)
unzip <path>             : extract .zip archive

gzip   ...               : create .gz archives and delete originals (-c don't delete)
gunzip ...               : extract .gz archives and delete originals (-c don't delete)

tar -cvf  <path> ...     : create .tar archive (no compression)
tar -xvf  <path>         : extract .tar archive
tar -czvf <path> ...     : create .tar.gz archive
tar -xzvf <path>         : extract .tar.gz archive

tar -cjvf <path> ...     : create .bz2 archive
tar -xjvf <path>         : extract .bz2 archive
```


### 3.4. Mobile app packages

*Mobile applications* usually can be downloaded only from a trusted source (like an *app store*). *App store* is a central managed marketplace for app developers to publish and sell mobile apps, i.e., the *app store* acts as *package manager*, and the *app store service* acts as a *package repository*.

- mobile apps are standalone software packages (i.e., contain all dependencies)
- apps on an *app store* have usually been through a security review and have been approved by the store owner
- apps on an *app store* are signed by the developer, and if the source code is changed, the signature becomes invalid
- in a business environment *enterprise app management* tools are used
- mobile apps can be installed from other sources too (*side-loading*)
- mobile apps store data in *cache* (so clearing cache will reset all the settings and delete all the user app data)


### 3.5. Devices and drivers

**Driver** is a software that helps a hardware device interact with an OS.

In Linux, everything is a file, even hardware devices. So when a device is connected to a computer, a [device file](https://en.wikipedia.org/wiki/Device_file) is created in the `/dev` [directory](https://en.wikipedia.org/wiki/Udev).

- most of the device files don't correspond to physical devices (e.g., `/dev/null`)
- common device types in Linux (see with `ls -l`):
    1. **character devices** (transmit data by characters, i.e., keyboards, mouses, etc.)
    2. **block devices** (transmit data by blocks, i.e., SSDs, USB drives, etc.)
- mass storage devices (e.g., hard and flash drives) are denoted as `/dev/sda`, `/dev/sdb/`, etc.
- most of the device drivers are a part of the *kernel*, and if not, there are *kernel modules* (installed like all  the other software in Linux)


### 3.6. OS updates

Installing latest system updates is a good practice to keep OS secure and get the newest features. In Ubuntu `sudo apt upgrade` will install the latest security updates, but won't upgrade the *kernel* and other core packages.

```
uname -r                 : show kernel release
sudo apt update          : update the list of packages for upgrade
sudo apt full-upgrade    : upgrade all packages including the kernel (or dist-upgrade)
```

[Content](#content)
-------------------------------------------------------------------------------
## 4. File systems

### 4.1. Review of file systems

A *file system* is used to keep track of files and file storage on a disk. The major operating systems have their own unique file systems:

- Windows uses **NTFS** by default, and Linux uses **ext4** (most common)
- for most file systems, cross OS support is minimal (e.g., Windows doesn't read *ext4*).
- there is also [**FAT32**](https://support.microsoft.com/en-us/help/154997/description-of-the-fat32-file-system) file system (used for flash drives):
    - supported by all three major operating systems
    - allows only for files smaller than 4 GB
    - max size of a file system is 32 GB


### 4.2. Partitions

A *storage device* can be divided into **partitions** (pieces of the device that can be managed independently). Partitions essentially act as separate sub-devices, but they all use the same physical device.

- file system can only be added on a partition
- different partitions of the same physical device can use different file systems
- when a file system is formated on a partition, it becomes a **volume**

**Partition table** is a component of a device that tells the OS how the device is partitioned (which are the boot partitions, space allocated for partitions, etc.)

There are two main *partition table schemes* which decide how to structure the information on partitions:

1. **MBR (master boot record)**
    - mostly used in Windows, slowly being replaced by GPT
    - max volume size is 2 TB
    - max four *primary* partitions on a device (can add more with *extended* and *logical* partitions)

2. **GPT (GUID partition table)**
    - max volume size is 8 ZB
    - max 128 partitions on a device (i.e., all partitions are *primary*)
    - UEFI booting is supported only for GPT devices


### 4.3. Disk partitioning, formatting and mounting

In Linux, *disk partitioning* and *file system formatting* can be done via GUI or with a few different partitioning terminal tools, e.g., with **parted**:

- supports MBR and GPT partitioning
- can be used in two modes: interactive (launched as a separate program) and command line (through shell)

```
sudo parted -l           : show info about connected storage devices and their partitions
sudo parted /dev/sdx     : run parted in an interactive mode for a selected device

(parted) print           : show info about storage device and its partitions
(parted) mklabel ...     : create device label (e.g., mklabel msdos/gpt)
(parted) mkpart  ...     : create partition (e.g., mkpart primary ext4 1MiB 5GiB)
(parted) quit            : quit from interactive mode

sudo mkfs -t <FS> <sdx#> : format selected partition with a file system
```

After a file system has been formatted it needs to be *mounted* to a directory (to make it accessible). Linux does this automatically, but it can also be done manually.

- manually mounted devices are unmounted on shutdown
- to automatically mount a device on startup modify `/etc/fstab` ([contains](https://en.wikipedia.org/wiki/Fstab) device UUIDs, or universally unique IDs; mount points, type of used file system, etc.)

```
sudo mount <sdx#> <path> : mount storage device to a directory
sudo umount <sdx#>       : unmount storage device (or <path> instead of </dev/sdx#>)
sudo blkid               : show UUIDs for storage devices (a.k.a block devices)
```


### 4.4. Virtual memory

**Virtual memory** allows OS provide the available physical memory (RAM) to the running applications. It creates a mapping between virtual and physical addresses. *Virtual memory* allows programs:

- not to worry about what portions of memory are used by other programs
- not to worry about where the data they use is located in RAM
- use more memory than physically available (by using a **swap area** on a hard drive) 

<p style="text-align:center;"><img src="data/virtual memory.png" width="400" title=" "></p>

When a particular *page of data* (data block) isn't being used by an application, it gets evicted (copied out of memory onto the hard drive). This way memory resources are used most efficiently, and if a program needs a page that's not accessed a lot, the OS can still get to it in *swap*.

Manually create swap partition on a storage device:
```
sudo parted /dev/sdx
(parted) mkpart primary linux-swap <start> <end>
(parted) quit
sudo mkswap /dev/sdx#
sudo swapon /dev/sdx#
```


### 4.5. Files and metadata

Linux uses a structure called **inode** to store and represent files and their metadata on a volume.

- inodes are stored in an *inode table*
- the inode stores everything about files except file names and the file data itself
- there are special types of files that provide access to other files:
    1. **Symbolic links**
        - point to another file by its name (i.e., if the name of the destination file is changed, the link will stop working)
        - create with `ln -s <path> <softlink> `
    2. **Hard links**
        - point to another file by its inode entry (i.e., if the name of the destination file is changed, the link will still work)
        - create with `ln <path> <hardlink> `
        - `ls -l` will show the amount of *hardlinks* a file has (third field)


### 4.6. Disk usage

In Linux, **disk usage** and **disk free** utilities can be used to monitor disk usage. Linux does a better job than Windows in avoiding fragmentation of data on hard disk drives, so [defragmentation is not needed](https://www.howtogeek.com/115229/htg-explains-why-linux-doesnt-need-defragmenting/).

```
du <path>                : show disk usage for a directory (-h human readable)
df                       : show free disk space (-h human readable)
```


### 4.7. File system repair

Data corruption could happen for lots of reasons:

- unsafe removing of a storage device (i.e., data might not to be transferred from buffer to a device in time)
- unexpected power shut downs
- system failures and software bugs

Linux file system has features that minimize the danger of data corruption, as well as, features that recover data when it gets damaged:

- [file system check](https://en.wikipedia.org/wiki/Fsck) utility will try to repair a file system (use `sudo fsck /dev/sdx` **only on unmounted devices!**)
- in some Linux distros `fsck` runs on a boot and tries to auto-repair any issues with the file system

[Content](#content)
-------------------------------------------------------------------------------
## 5. Process management

### 5.1. Processes

**Program** is an application that a user can run.

**Process** is a program that's executing (i.e., user can have many processes of the same program running at the same time, e.g., browser tabs of a web browser).

- when Linux boots, OS kernel starts `init` process (`PID = 1`), which starts up all other processes
- in Linux, processes have a *parent-child* relationship, i.e., every process has a parent (child process inherit some things like variables and settings, i.e., environment)
- when processes complete their task, they will usually terminate automatically
- Linux processes can't operate independently of their parents (unlike in Windows), i.e., if user terminates a parent of a process, it will be terminated too


### 5.2. Process monitoring

In Linux processes can be monitored:

1. by viewing the files in `/proc` directory (since everything in Linux has a file, including processes)
2. with `ps` [utility](https://man7.org/linux/man-pages/man1/ps.1.html)

```
ps                       : show short list of processes
ps -x                    : show list of processes
ps -ef                   : show extended list of processes
```

- Info for `ps -x`:
    - **PID** (process ID)
    - **TTY** (terminal associated with the process)
    - **STAT** (process status: R for running/waiting to run, T for suspended, S for interruptible sleep)
    - **TIME** (total CPU time the process has taken up)
    - **Command** (name of the command that's running)

- Info for `ps -ef`:
    - **UID** (user ID of the user who launched the process)
    - **PID** (process ID)
    - **PPID** (parent process ID)
    - **C** (number of children)
    - **STime** (start time of the process)
    - **TTY** (terminal associated with the process)
    - **TIME** (total CPU time the process has taken up)
    - **CMD** (name fo the command that's running)


### 5.3. Process management

Sometimes user might want to interrupt a process before it fully completes. **Signals** are used for that purpose, they can be generated through other processes and software, or with keyboard shortcuts. Most common *signals* in Linux:

- **SIGINT**
    - interrupt the process
    - keyboard shortcut: <kbd>Ctrl</kbd> + <kbd>C</kbd>

- **SIGTERM**
    - terminate the process (and give some time to clean up the resources to avoid file corruption)
    - with `kill <PID>`

- **SIGKILL**
    - terminate the process (immediately)
    - with `kill -KILL <PID>`

- **SIGTSTP**
    - suspend the process (to continue it later)
    - with `kill -TSTP <PID>`
    - keyboard shortcut: <kbd>Ctrl</kbd> + <kbd>Z</kbd>

- **SIGCONT**
    - continue suspended process
    - with `kill -CONT <PID>`


### 5.4. Jobs

In Linux, **job** is a task that has started running and not yet completed.

- each job is assigned with a sequential *job ID*
- types of job statuses:
    1. *foreground* (command occupies the terminal until it completes)
    2. *background* (command runs without occupying the terminal)
- user can turn *foreground* jobs into *background* jobs by suspending them, i.e., with a <kbd>Ctrl</kbd> + <kbd>Z</kbd> shortcut, or with a `bg` command
- user can run a program in a *background* mode with a `<program> &` command

```
jobs                     : list all jobs
fg %<JID>/%<str>         : place job into the foreground
bg %<JID>/%<str>         : place job in the background
```


### 5.5. Resource monitoring

In Linux, user can monitor system resources use with several tools:

- `uptime` (brief info)
    - shows info about the current time and how long system's been running
    - shows how many users are logged on
    - shows computer's [load average](https://en.wikipedia.org/wiki/Load_(computing)) (average CPU load in 1, 5, and 15 minute intervals)

- `top` (full info)
    - shows the processes that are using the most resources
    - returns *idle* (a quick snapshot of total tasks running), CPU usage, memory usage, etc.
    - <kbd>Q</kbd> key to quit

- `htop` (similar to `top`)

- `lsof`
    - list open files and processes that are using them

[Content](#content)

-------------------------------------------------------------------------------
## 6. Operating systems in practice

### 6.1. Remote connection

**SSH (secure shell)** is a protocol used to securely connect to computers remotely.

- *SSH client* needs to be installed on a user computer, and *SSH server* on a host machine (popular programs: OpenSSH and PuTTy)
- *SSH server* doesn't need to be a physical machine, it can be just a software that's running as a background process
- connect with `ssh <user>@<host>` (OpenSSH)
    - user has to have an account on a host machine
    - can access host using an *IP address* or a *host name*
    - can specify a port with `-p <port>` (`22` by default for SSH)
- when user connects to a remote machine for the first time, they will be asked to verify the authenticity of a host, and after confirmation host will be added to the list of known hosts
- SSH *authentication keys* can be used instead of passwords (more secure)
- users can transfer data between computers through SSH tunnel using **scp (secure copy)** utility or file managers (e.g., filezilla):
    ```
    scp <user>@<host>:<path1> <path2> : copy server → client
    scp <path1> <user>@<host>:<path2> : copy client → server
    ```
- another option for secure remote connections: VPN


### 6.2. Logs

In most systems, there is a service that runs in the background and constantly writes events to logs. In Linux, logs are stored in the `/var/log` directory.

- some of the log files:
    ```
    /var/log/syslog      : everything (except off events)
    /var/log/auth.log    : authorization and security-related events
    /var/log/kern.log    : kernel messages
    /var/log/dmesg       : system startup messages
    ```
- logs are deleted after some period of time to save storage space (`lofrotate` is a utility for *log rotation*)
- in the case of a set of machines the *centralized logging* is used
- `/var/log/syslog` includes:
    1. time stamp of the event (can be in *Unix/epoche time* format, i.e., number of seconds since `1970-01-01 00:00`)
    2. host name of the machine the event occurred on
    3. service that the log event is referring to
    4. the event that occurred
- can search for specific events by filtering
- watch logs in real time: `tail -f /var/log/syslog`


### 6.3. OS deployment

Installing an OS on a large number of machines using traditional methods (e.g., with a USB stick) can be very time consuming, so other methods are used instead:

1. **Disk cloning**
    1. Unmount device: `umount /dev/sdx`
    2. Create an image: `sudo dd if=dev/sdx of=<path.img> bs=100M`

2. **Network initiated deployment**
    - request the images directly from the network
    - there are ways to use custom images too


### 6.4. Networking

```
nmcli networking on/off  : networking on/off
nmcli radio wifi on/off  : wi-fi on/off
ip a                     : show local IP address
curl ifconfig.me         : show IP address

ping       <domain>/<IP> : send an echo request
traceroute <domain>/<IP> : trace route to the destination
nslookup   <domain>/<IP> : resolve a domain name

wget <options> <link>    : download a file
                           --spider      - check file availability
                           -P <path>     - specify download directory
                           -O <path>     - specify name of a file
                           -i <file.txt> - download files using links in a text file
                           -r -l <depth> - download recursively
                           -A <ext1>,... - list of allowed file extensions
                           -R <ext1>,... - list of rejected file extensions
```


### 6.5. Aliases

Users can create *aliases* for their most used commands. Aliases can be *temporary* (for a current terminal window) or *permanent* (modify `~/.bashrc`).

```
alias                    : list all aliases
alias <alias>="<com>"    : create alias
unalias <alias>          : remove alias (-a all)
```


### 6.6. Environment variables

In Linux, *environment variables* are a set of dynamic named values, that are used to store system settings (i.e., path to home directory, language settings, terminal settings, etc.). They are used by applications launched in shells or subshells.

- *environment variables* have the following format:
    ```
    KEY=value
    KEY="value"
    KEY=value1:value2
    ```
- *environment variable* types:
    1. **system-wide environment variables**
    2. **session-wide environment variables**
    3. **shell variables**
- show and modify *environment variables* values:
    ```
    env                  : list all env variables (or printenv)
    set                  : list all env and shell variables
    env  $<var>          : print env variable value (or printenv <var>)
    echo $<var>          : print env or shell variable value

    <var>="<val>"        : assign value to a shell variable
    export <var>="<val>" : assign value to an env variable
    unset <var>          : unset env or shell variable
    ```
- to make changes in *environment variables* persistent user needs to modify bash configuration files:
    1. for *system-wide variables* modify `/etc/environment` in the `VAR="val"` format
    2. for *session-wide variables* modify `~/.bashrc` in the `export VAR="val"` format (user-specific)

[Content](#content)

[Contents](../README.md#contents)