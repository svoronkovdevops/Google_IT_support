# OS

## Content

[Navigating the System](#navigating-the-system)

[Users and Permissions](#users-and-permissions)

[Package and Software Management](#package-and-software-management)

[Filesystems](#filesystems)

[Process Management](#process-management)

[Operating Systems in Practice](#operating-systems-in-practice)

[Content](#content)

[Courses list](README.md#contents)


# Navigating the System

## Basic Commands

- The command line interpreter in **Linux** is called a **shell**, and the language that we'll use to interact with this shell is called **Bash**.

#### Directories

- The **file system** controls how data is stored and retrieved in a computer.
- Files and folders are organized in a hierarchical directory tree.
- A main directory branches off and holds other directories and files.
  - We call the location of these files and directories **paths**.

#### PowerShell Commands
A **wildcard** is a character that's used to help select files based on a certain pattern.
  - The asterisk `*` represents the wildcard

- The `-recurse` parameter lists the content of the directory
  - If there are any subdirectories in that listing, it will recurse (or repeat) the directory listing process for each of those subdirectories.
- `-verbose` will output one line for each file of the directory being copied.
  - Unlike in Bash, these flags go after the destination in PowerShell

- The command to remove files and directories is `rm` (remove). 
  - You can append with the `-force` parameter, to remove protected or important files.

To delete a folder and its contents, remember to append with the recurse parameter.
  - Ex: `rm ~ /misc_folder -Recurse`


### Windows

The main directory in a Windows file system is called the **C Drive**

- In Windows, subdirectories are backslashes `\`, unlike Linux, which uses forward slashes `/`
- An **alias** is a nickname for a command
  - **parameters** tag onto a command, to specify additional options

- An **absolute path** is one that starts from the *main directory*; a **relative path** is the path from your *current directory*.



### Linux

The main directory in a Linux file system is called the **root directory** (`/`)

- All files and folders in a Linux system are part of a bigger tree-like structure, rooted at `/` (aptly called *root*)
- All file names are case sensitive


- Similar to Windows command parameters, a **flag** is a way to specify additional options for a command.
  - An example is the `--help` flag, which shows useful information on how to use a command.

#### Appending commands
- `ls -la` is the same thing as `ls -l -a`, and both work the exact same way.
- However, the order of the flag determines which order it goes in.

#### Bash Commands
- `-r` is the flag for recursive copy
- To delete a folder and its contents, remember to use the recurse parameter.
  - Ex: `rm -r misc_folder`


## File and Text Manipulation

Notepad++ can search for file content across directories (`ctrl` + `shift` + `f`)

#### PowerShell

`-Head` and `-Tail` are useful for viewing the first (or last) lines in a file.

To figure out the difference between PowerShell commands and aliases, use the command `Get-Alias x` (where x is the command you're determining)
- PowerShell commands are long and descriptive, which do help explain; but they require extra typing.

There are three ways you can run commands in Windows:
1. PowerShell commands
2. Alias name (Bash command)
3. cmd.exe 
  - `/?` serves as get-help for cmd.exe (ex: `dir /?`)

`Select-String` is a powerful tool when combined with wildcards

- The `-Filter` parameter will filter the results for file names that match a pattern.
  - Ex: `ls 'C:\Program Files\' -Recurse -Filter *.exe`

In PowerShell, `echo` is an alias for `Write-Output`


#### Bash

- `less` is used for viewing large files in the terminal
  - You can navigate with up and down; page up/down; `g` moves to the beginning of a text file; `G` moves to the end of a text file; 
  - `/word_search` allows you to search for a word or phrase
  - `q` allows you to quit less and return to the shell
 - `head` and `tail` operate as they do in PowerShell

In Bash, you can search for words within files that match a certain pattern using the `grep` command.


### I/O Streams

#### Windows

Each process in Windows has three different streams:
- Standard in / `stdin`
- Standard out / `stdout`
- Standard error `stderr`

The CLI input you provide through the keyboard goes to the `stdin` stream; the process then communicates back to you by putting data into the `stdout` stream, which the CLI prints onto your screen.

The `>` is the **redirector operator**, which lets us change where we want our standard output to go.
  - Instead of sending it to your screen, you can send it to a file.

The `>>` is another redirector operator, which can append information to an existing file (rather than overwrite it).

The `|` is the **pipe operator**, which can send the output of one command to the input of another command.
  - An example would be searching for a string in wildcard files, then extracting that string to a new file.
  - Ex: `cat words.txt | Select-String st > st_words.txt

You can redirect standard error to **$null**, which is like a black hole.



#### Linux

Linux uses the same I/O streams of `stdin`, `stdout`, and `stderr`

The **standard in redirector operator** is `<` (less-than sign), and gets input from a file, not from the keyboard.
  - Ex: `cat < file_input.txt`

The **standard error redirector operator** is `2>`, used to redirect the error messages of some output.

`/dev/null` serves as the $null variable for Linux


**Regular expressions** are used to help you do advanced pattern-based selection.

### Create, Modify, and Remove Files/Folders in Linux

#### Creating directories
- Directories (folders) in Linux are created using the `mkdir` command. 
- The command takes the directory name as the argument
  - Ex: `mkdir dir_name`
- Multiple directories can be supplied as arguments, and mkdir will create all of them:
  - Ex: `mkdir dir1 dir2 dir3`
- mkdir can take three options:
1. `-p` allows mkdir to create parent directories if they don't exist
2. `-m` (mode) used to set permissions of directories during creation
3. `-v` run command in verbose mode

#### Removing empty directories
- To remove empty directories, use the `rmdir` command.
  - The name of the directory being removed is passed as an argument
    - Ex: `rmdir dir_name`
- Like creation, multiple directories can be passed as arguments.
  - Ex: `rmdir dir1 dir2 dir3`
- rmdir only takes one option:
  - `-p` remove parent directories, but only if they're also empty

#### Creating files
- The touch command is used to change the modification and access times of a file.
- If the file doesn't exist, the command is used to create a file with default permissions.
  - Ex: `touch empty_file`
- `-c` do not create file if it doesn't exist

### Copying, moving, and deleting files and directories

- You can use a "dot" to copy or move files to the current directory.
  - Ex: `user@pc /home/user/Pictures $ mv /home/user/Images/Vacation.jpg .`

#### Searching in files
- **grep** is a super-powerful Linux command used to search through files for strings. 
- grep has many options and flags:
  - `-r` search recursively
  - `-w` match the whole word
  - `-n` only in line number
  - `-e` match pattern
  - `--include` and `--exclude` files in the search
  - `--include-dir` and `--exclude-dir` directories in the search
- Ex: `grep -rw /home/user/Downloads -e "vacation"`


[Content](#content)
----------------------------------------------------------------------------Users and Permissions-------------------------------------------------------------------------------


# Users and Permissions

## Users and Groups

### Users, Administrators, and Groups, Oh My!

There are two different types of users:
1. **Standard users**
    - One who is given access to a machine but has restricted access to do things like install software or change certain settings.
2. **Administrators**
    - A user that has complete control over a machine.

Users are put together in **groups** according to levels of access and permissions to carry out certain tasks. 
- These tasks depend on what the computer's administrator deems to be appropriate.
- An administrator could give different access and settings based on the type of group a user is in.


### Windows: View User and Group Information

To view user and group information in Windows, use the Computer Management tool/application. 
- All of the essential settings that administrators need to change are found in the Computer Management tool.
- In an enterprise environment, you can manage multiple machines in something called a domain.
  - A **Windows domain** is a network of computers, users, files, etc that are added to a central database.

#### Computer Management (tool)
Underneath this menu, we have System Tools:
- Task Scheduler
  - This lets you schedule programs and tasks to run at certain times (like automatically shutting off the computer at 11:00pm every night)
- Event Viewer
  - This is where our system stores its system logs.
- Shared Folders
  - This shows the folders that different users on the machine share with each other.
- Local Users and Groups
  - This is where we'll be doing our user and group management.
- Performance
  - This shows monitoring for the resources of our machines (like CPU and RAM)
- Device Manager
  - This is where we go to manage devices to our computer like our network cards, sound cards, monitors, and more.
- Storage
  - A submenu for Disk Management.
- Services and Applications
  - This shows us the programs and services that we have available on the system (such as enabling/disabling DNS).

- **User access control (UAC)** is a feature in Windows that prevents unauthorized changes to a system.
  - These changes must be authorized by an administrator, instead.


### Linux: Users, Superusers, and Beyond

Linux has a few differences from Windows in how it labels users:
- Standard users
- Administrators
- Root user

#### Root User
- This is the first user that gets automatically created when a Linux operating system is installed.
- This user has all the privileges on the OS -- the superuser.
- Technically, there is only one superuser or root account;
  - But anyone granted access to use these powers can be called a superuser too.
- Logging in as root is dangerous; 
  - Instead, you can tell the shell you want to run just a single command as root. (Similar to Windows UAC.)
  - This is done with `sudo`, "superuser do"

#### Viewing memberships
You can see who has access to using `sudo` by viewing the `/etc/group` file, as well as viewing memberships for all groups.

Each user line has four fields (separated by colons):
1. The first field is the group name
2. The second field is the group password, usually an encrypted `x`
3. The third field is the group ID
4. The last field is a list of users in the group

**If you want to view the users on the machine**, the file is stored in `/etc/password`, not `/etc/user`.
- In this file, the first three fields (for each user) have significance:
  1. Username
  2. Password (again, encrypted)
  3. User ID (UID)
    - Root has a UID of zero.


### Windows: Passwords

If you're managing other people's accounts on a machine, you shouldn't know what their password is. Instead, you want the user to enter the password themselves.

#### Resetting a password
You can reset a password with Windows's Computer Management tool.
- Under "Local Users and Groups," right-click on a username; then click on "Properties."
  - Then, check the box for "User must change password at next logon."

You can also set a password for them manually, by right-clicking and selecting "Set password." But this isn't the best idea, and there are caveats (like using access to certain credentials).

To change a local password in PowerShell, you can use the DOS-style `net` command. (There is a native PowerShell command to do this, but it requires some scripting.)

`net` does many things, and changing local user passwords is one of them.
  - Since it's an old DOS command, you can use the `/?` parameter to get help in the CLI.
- To change a password for a user, the command is `net user USERNAME 'password'`
  - But the best way to do this is to use an asterisk `*` instead of writing the password out on the command line.
  - Using an asterisk will pause the command and prompt you to enter your password.
  - This is superior, because it maintains privacy;
    - Commands run on machines are usually recorded in a log file, that's sent to a central logging service
    - Thus, password secrecy is compromised
- But it's still best to keep other users' passwords private, even if you're an admin;
  - So instead, run ``net user USERNAME /logonpasswordchg:yes`


### Linux: Passwords
To change passwords in Linux, all you need to do is run the `passwd` (the password command).

If you're managing a computer and want to force a standard user to change their password, you can use the `-e` ("expire") flag with the command: `sudo passwd -e USERNAME`


### Windows: Adding and Removing Users

Adding a new user through the GUI is as simple as right-clicking and selecting "New User."
- Then you can set the username, full name, and password
  - You can also force the user to change their password at their next logon

In PowerShell, you can use `net user username * /add` to create a new user; but this will let you set their password credentials. So amend this with `net user USERNAME /logonpasswordchg:yes`
- Or combine the commands:
  - `net user USERNAME pa5sw0rd /add /logonpasswordchg:yes`

Deleting a user through the GUI is likewise a simple right-click affair.

In PowerShell, you can remove a user through the command `net user USERNAME /del`


### Linux: Adding and Removing Users

- To add a new user in Linux, run the command `sudo useradd USERNAME`
  - This will set up basic configurations for the user, and set up a home directory.
- Combine it with the password command to make them change their password, for better practice.
- To remove a user, simply run `sudo userdelete USERNAME`


### Mobile Users and Accounts

- In mobile devices, the initial account that you use during setup is called the *primary account*
  - This account is used to create a user profile for you on the device
- The user profile is like your user account in a mobile device, containing accounts, preferences, and apps.

**Single sign-on (SSO)** means apps will allow you to authenticate using an account that you're already signed into (such as iOS or Android accounts).

- Some smartphones use fingerprint sensors, facial recognition, or other kinds of biometric data to grant access to the device.
  - **Biometric data** is something about you that's unique to you, like a fingerprint, voice, or face.

**Mobile device management (MDM)** systems are used by organizations to protect business data, and are used to apply and enforce rules about how the device has to be configured and used.


## Permissions

### Windows: File Permissions

In Windows, files and directory permissions are assigned using **Access Control Lists (ACLs)**. One such type are **Discretionary Access Control Lists (DACLs)**.

Windows files and folders can also have **System Access Control Lists (SACLs)** assigned to them. SACLs are used to tell Windows that it should use an event log to make a note of every time someone accesses a file or folder.

#### Discretionary Access Control Lists (DACLs)
- A DACL is like a note about who can use a file, and what they're allowed to do with it.
- Each file/folder will have an owner, and one or more DACLs.

There are multiple DACL permissions you can assign to each user group:
- Read
  - Lets you see that a file exists, and allows you to read its contents.
  - It also lets you read the files and directories in a directory.
- Read and Execute
  - Lets you read files, and if the file is an executable, you can run the file.
  - R&E includes Read, so if you select this option, Read will automatically be selected, too.
- List folder contents
  - An alias for Read & Execute on a directory (checking one will check the other)
  - Means you can read and execute files in that directory
- Write
  - Lets you make changes to a file
  - You can have write access to a file without having read permission to that file
  - Also lets you create subdirectories, and write to files in the directory
- Modify
  - An umbrella permission that includes read, execute, and write
- Full control
  - A user or group with full control can do anything they want to the file!
  - Includes all of the permissions of Modify, and adds the ability to take ownership of a file and change its ACLs


### Linux: File Permissions

There are three different permissions you can have in Linux:
1. Read
  - This allows someone to read the contents of a file or folder.
2. Write
  - This allows someone to write information to a file or folder.
3. Execute
  - This allows someone to execute a program.

In the command line, the permission column is represented by 10 bits.
- The first is the file type (a `-` means the file is just a regular file; a `d` represents a directory)
- The next 9 bits are the actual permissions, grouped in sets of three (trios):
  - The first trio refers to the permission of the owner of the file
  - The second trio refers to the permission of the group that this file belongs to
  - The last trio refers to the permission of all other users
- `r` stands for "readable," `w` stands for "writable," and `x` stands for "executable"
- Like in binary, if a bit is set, then we say that it's *enabled*.
  - If a bit is a dash, it's *disabled*; if it's anything other than a dash, it's enabled


### Windows: Modifying Permissions

When using `icacls`, surround its parameters in single quotes (when using PowerShell.exe); when running in command.exe, you'll need to remove the single quotes for them to work.

#### Guest users
- This is a special type of user that's allowed to use the computer without a password. 
- Guest users are disabled by default. 
- You might enable them in very specific situations.

*Authenticated Users* are users with password credentials, unlike Guest Users.


### Linux: Modifying Permissions

Permissions are changed in Linux through the `chmod`, or "change mode" command.

#### Symbolic Format
- `u` the file/directory owner
- `g` the group the file belongs to
- `o` all other users

To add or remove permissions, just use a `+` or `-` to indicate who the permission affects.

#### Numeric Format

| Permission | Symbolic | Numeric |
|:----------:|:--------:|:-------:|
|    read    |     r    |    4    |
|    write   |     w    |    2    |
|   execute  |     x    |    1    |

- Add the numbers together to represent the permissions.
- Example: `chmod 754 my_cool_file`
  - The first number (7) is the owner's permission, which is read+write+execute
  - The second number (5), is the group's permission, which is read+execute
  - The third number (4) is all other users, which is read only.


### Windows: Special Permissions

Most of the permissions covered [in these notes] so far are *simple permissions*.

**Simple permissions** are actually sets of special, or specific permissions.
- For example, when you set the Read permission, you're actually setting multiple special permissions.

Usually, simple permissions will get the job done. But, sometimes you need to create a file or folder with special directories.

Some `icacles` permissions you can set:
- `WD` Write Data/Create Files
- `AD` Append Data/Create Folders
- `S` Synchronize

NTFS DACLs can be complicated, but it can also let you create really powerful sets of permissions customized to your exact needs.


### Linux: SetUID, SetGID, Sticky Bit

The **SetUID** bit is used to allow a file to be run as the owner of the file.
- The symbolic bit is a `s` and the numeric bit is a `4`

The **sticky bit** allows the file to be modified by anyone, but only removed by the owner or root.
- The symbolic bit is a `t` and the numeric bit is a `1`


[Content](#content)



---------------------------------------------------------------------------------------Package and Software Management-----------------------------------------------------------------------------

# Package and Software Management

## Software Distribution

### Windows: Software Packages

- In Windows, software is usually packaged as a `.exe` (executable file)
- **Executable files (.exe)** contain instructions for a computer to execute when they're run.
  - They're created according to Microsoft's *portable executable (PE) format*.
  - They include instructions for the computer to perform, text, computer code, images, and possibly an `.msi file`.
- A **Microsoft install package (.msi)** is used to guide a program--called the *Windows Installer*--in the installation, maintenance, and removal of programs on the Windows operating system.
  - Besides using the GUI setup *wizard* to guide the user in installation, the Windows Installer also uses the .msi file to create instructions on how to remove the program, if so desired.

Executables can simply contain a .msi file; or they can be used as stand-alone, custom installers without .msi or use of the Windows Installer.
  - For precise, granular control over the actions Windows takes when installing software, a custom installer may be better.
  - But while Windows Installer has strict rules about how software gets installed, it does handle a lot of the setup and bookkeeping for you.

As of Windows 8, Microsoft introduced a platform to distribute programs, called the Windows Store (later renamed the **Microsoft Store**). 
- The store is an application repository (or warehouse), where you can download and install universal Windows platform apps.
- These programs use a format called **APPX** to package their contents and act like a unit of distribution.


### Linux: Software Packages

There are many different Linux distributions, each with different package types.
- For example, Red Hat uses `.rpm` (Red Hat Package Manager) packages.
- Ubuntu uses **Debian** packages.
  - **Debian** packages as a `.deb` file for Debian Linux (on which Ubuntu is based)

- To install a Debian package, you'll need to use the `dpkg` ("Debian package") command.
  - Ex: `sudo dpkg -i SOFTWARE.deb`
- You can list the Debian packages installed on your machine with `dpkg -l`
- Or, you could search for and list them with `dpkg -l | grep SOFTWARE`


### Mobile App Packages

- Software for mobile operating systems is distributed as *mobile applications*, or *apps*.
- Mobile OS also require their apps to come from a source the device has been configured to trust--an app store.
- **App stores** are a central, managed marketplace for app developers to publish and sell mobile apps.
  - The **App store app** acts like a package manager;
  - The **App store service** acts like a package repository
  - Apps published through an app store are signed by the developer; and an OS is configured to only trust code that's been signed by publishers it recognizes.

**Enterprise app management** allows an organization to distribute custom mobile apps, developed by and for the organization and unavailable to the general public.
- Enterprise apps are signed with an enterprise certificate that has to be trusted by the device installing the application.

**Side-loading** is where you install mobile apps directly, without using an app store.
- Side-loading packages is riskier than installing through an app store
- You would generally only do this if you're an app developer

Mobile apps are standalone software packages, so they contain all their dependencies.

Mobile apps are assigned a specific storage location for their data.
- Anything that's changed or created with that app will end up in that app's assigned storage location, aka **cache**.
- So a mobile app factory reset is as simple as deleting/clearing the cache.


### Windows: Archives

An **archive** is comprised of one or more files that's compressed into a single file.

**Package archives** are the core or source software files that are compressed into one file.

When we install software from a source archive, it's referred to as *installing from source*.

Popular archive types you'll see include `.tar`, `.zip`, and `.rar`.
- To install software found in an archive, you first have to extract the contents of the archive (so you can see the files inside)


**7-zip** is a popular open-source tool for archiving and unarchiving different file types.


### Linux: Archives

7-Zip is also available for Linux. You can extract a file with it, using the `7z -e FILE` command.

Among the many archival tools, one already installed on most Linux distros is the `tar` command.


### Windows: Package Dependencies

**Having dependencies** is counting on other pieces of software to make an application work, since one bit of code depends on another, in order to work.

A **library** is a way to package a bunch of useful code that someone else wrote.
- This code is bundled together into a single unit.
  - Programs that want to use the functionality that the code provides can tap into it if they need to.
- In Windows, these libraries are called **dynamic-link libraries (DLL)**

The same DLL can be used by lots of different programs; it doesn't need to be loaded into memory for each application that wants to use it. Thus, less overall memory is used.

#### SxS
Most shared libraries and resources in Windows are managed by something called **side-by-side assemblies**, or **SxS**.
- Most of these shared libraries are stored in a folder at `C:\Windows\WinSxS`
- If an application needs to use a shared library to perform a task, that library will be specified in something called a **manifest**.
  - This tells Windows to load the appropriate library from the SxS folder. 
- SxS also supports access to *multiple versions of the same shared library* automatically.

You can locate software and its dependencies directly from the command line through PowerShell's `Find-Package` cmdlet.

> A **cmdlet** is basically the name we give to Windows PowerShell commands that use the `verb-noun` format.


### Linux: Package Dependencies

Know that if you install a standalone package, you won't automatically install its dependencies.

**Package managers** come with the works to make package installation and removal easier, including installing package dependencies.



## Package Managers

### Windows: Package Manager

A **package manager** makes sure that the process of software installation, removal, update, and dependency management is as easy and automatic as possible.

> `apt` is actually a package manager for the Ubuntu operating system.

**Chocolatey** is a third-party package manager for Windows.
- It's not written by Microsoft
- It lets you install Windows applications from the command line
- It's built on existing Windows technologies like PowerShell
- It lets you install any package or software that exists in the public Chocolatey repository


### Linux: Package Manager Apt

The **Advanced Package Tool** `apt` is used to extend the functionality of the package.
- It makes package installation easier
- It installs package dependencies for us
- Makes it easier for us to find packages that we can install
- It cleans up packages we don't need
- And more!

`apt` grabs the dependencies that a package requires automatically, and asks if you want to install it.

With a *package repository*, you don't have to manually search for each and every software you want online.

**Repositories** are servers that act like a central storage location for packages.
- You can add a software's link to your own machine, so it references that package or list of packages
  - An example is the `Register-PackageSource` cmndlet in PowerShell
  - In Ubuntu, the repository source file is `/etc/APT/sources.list`
- In Linux, there are also special repositories called PPAs:
  - A **Personal Package Archive (PPA)** is a software repository for uploading source packages to be built and published as an **Advanced Packaging Tool (APT)** repository by Launchpad.
    - Launchpad is a website owned by Canonical Limited, and its servers host PPAs.
  - Use caution when using a PPA instead of the original developer's repositories. 
    - The software can be defective, or even malicious.

You can update your package repositories with the `apt update` and `apt upgrade` commands.
- `apt update` updates the list of packages in your repositories, fetching the latest software available
  - But it won't install or upgrade, which means you need to use...
- `apt upgrade` will install any outdated packages for you automatically

You can use the `apt --help` command to learn more about the commands available with APT. 


## What's happening in the background?

### Windows: Underneath the Hood

When you click on an installation executable, what happens next depends on how the developer of the program has set their application app to be installed.

- If the `.exe` contains code for a custom installation that doesn't use the Windows installer system, then the details of what happens under the hood will be mostly unclear.
- Although you can't read the instructions the developer has written, you can use certain tools to check out the actions the installer is taking.
- The **Process Monitoring** program provided by the Microsoft CIS internals toolkit is one such way.
  - The program shows you any activity the installation executable is taking, like the files it writes and any process activity it performs.

#### MSI Files
- MSI files are closed source, so you won't be able to peek at the source code.
- MSI files are a combination of databases that contain installation instructions in different tables along with all the files, objects, shortcuts, resources, and libraries the program will need all grouped together.
- The Windows installer uses the info stored on the tables in the MSI database, to guide how the installation should be performed.
- Windows installer keeps track of all action it takes, and creates a separate set of instructions to undo them (this is how you can easily uninstall the program)

**Orca**, or `orca.exe` is a tool that Microsoft provides. It's part of the Windows software development kit (SDK), and helps you edit or create Windows installer packages.


### Linux: Underneath the Hood

Linux installs software directly from source code, so the process is far more straightforward than in Windows.
- A setup script is a script file that will run a bunch of tasks on the computer in order to set up the package.
  - A sample script can contain program instructions that compile code into machine instructions, compile binary to `/bin` directory, or create a folder to `/home/`, etc
- The README is a standard file contained in source archives, which has information about the archive.


## Device Software Management

### Windows: Devices and Drivers

Remember that a **driver** is used to help our hardware devices interact with our operating system.

In Windows, Microsoft groups all of the devices and drivers on the computer together in a single Microsoft management console called the **Device Manager**.

- Windows uses the **Plug and Play (PnP)** system, to automatically detect new hardware, which it then identifies and installs the appropriate software to manage it.
- Most vendors or computer hardware manufacturers will assign a special string of characters to their devices called a **hardware ID**.
- When Windows notices that a new device has been connected, the first thing it will do is ask the device for its hardware ID.
  - Once Windows has the hardware ID of the new device, the OS uses that ID to search for the right driver for the device.
  - It looks in a few places for the driver; starting with a local list of well-known drivers, then going onto Windows Update or the Driver Store.


### Linux: Devices and Drivers

- In Linux, everything is considered a file, even hardware devices.
- When a device is connected to the computer, a device file is created in the `/dev` directory.
  - This directory contains many devices, but not all of them are actual physical devices.
- **Character devices**, like a keyboard or mouse, transmit data character by character.
- **Block devices**, like USB drives, hard drives, and CD-ROMs transfer blocks of data.

Remember that the first bit you see in a `ls -l` command is the type of file. Among these are:
- `-` for regular file
- `d` for directory
- `b` for block device
- `c` for character device

Some files start with `/dev/sda` or `/dev/sdb`. SD devices are mass storage devices like hard drives, memory sticks, etc. 
- The A after SD just means the device was detected by th ecomputer first
  - So you could see `sda`, `sdb`, `sdc`, etc

#### Device Drivers
- Device drivers aren't stored in the `/dev` directory; sometimes they're part of the Linux kernel.
- A lot of modern hardware support is built into the kernel; so that when you plug in a device, it automatically works.
- But if there are devices that don't have support built into the kernel, they most likely have something called a **kernel module**.
  - A kernel module extends the kernel's functionality, without the developer actually touching the kernel (an intimidating prospect for many developers)
  - Not all kernel modules are drivers.
  - If you need to install a kernel module for a specific type of device, you can install it the same way you install all other software in Linux.


### Windows: Operating System Updates

A **security patch** is software that's meant to fix up a security hole.

The Windows Update Client service runs in the background on your computer to download and install updates and patches for your operating system. It does thsi by checking with the Windows Update servers at Microsoft, periodically.

As of Windows 10, Windows updates in a cumulative way. Every month, a package of updates and patches is released that supersedes the previous month's updates.


### Linux: Operating System Updates

Linux keeps its operating system up to date through updating the kernel.

- To view which kernel version you have, run `uname -r`
- To update the kernel and other packages, run `sudo apt update` and `sudo apt upgrade`

[Content](#content)

-----------------------------------------------------------------------------------------------------------------Filesystems-----------------------------------------------------------------


# Filesystems

## Filesystem Types

### Review of Filesystems

Recall that a **filesystem (fs)** is used to keep track of files and file storage on a disk.
- Without a filesystem, the operating system wouldn't know how to organize files.

Windows uses the NTFS filesystem; and Linux generally uses ext4. But these are not cross-operating.
- A USB drive using NTFS can be used by both Windows and Ubuntu Linux
- However, a USB drive using ext4 will only work on Ubuntu, not with Windows

Filesystems like **FAT32** support reading and writing data to all three major operating systems. 
- However, it doesn't support files larger than 4 GB
- And the size of the filesystem can't be larger than 32 GB


### Disk Anatomy

A **storage disk** can be divided into something called *partitions*.
- A **partition** is just a piece of the disk that you can manage.
- When you create multiple partitions, it gives you the illusion that you're physically dividing a disk into separate disks.

To add a filesystem to a disk, first you need to create a partition. Usually, we just have a single partition for our OS; but it's not uncommon to have multiple partitions for different uses.

When you format a filesystem on a partition, it becomes known as a **volume**. (Volume and partition are mistakenly used synonymously, so know that there is a difference.)

#### Partition Table
The other component of a disk is a *partition table.* 
- A **partition table** tells the OS how the disk is partitioned.
- The table will tell you which partitions you can boot from, how much space is allocated, etc

There are two main partition table schemes that are used: MBR, or GPT.

**Master Boot Record (MBR)** is a traditional partition table, mostly used in Windows OS. 
- It only lets you have volume sizes of 2 TB or less.
- It also uses something called *primary partitions*.
  - You can only have four primary partitions on a disk.
  - If you want to add more, you have to convert a primary partition into an *extended partition*
    - And inside the extended partition, you can make a *logical partition*
- MBR is an old standard, slowly being phased out by GPT.

**GUID Partition Table (GPT)** is becoming the new standard for disks.
- You can have a volume size greater than 2 TB;
- It has only one type of partition;
- And you can make as many of them as you want on a disk.
- UEFI (the emerging BIOS standard) requires the GPT.


### Windows: Disk Partitioning and Formatting a Filesystem

#### Through GUI

Windows ships with a native tool called Disk Management Utility.
- You can access it through the GUI, right-clicking on "This PC" to "Manage," then clicking "Disk Management"

Quick format vs. full format
- In a full format, Windows will do a little extra work to scan the disk or USB drive for errors or bad sectors
- This extra work will make the formatting process take longer

Enable vs. disable file/folder compression
- If you enable, your files and folders will take up less space on the disk;
- But compressed files will need to be expanded when you open them, which puts more work on the computer's processor

#### Through command line

Disk manipulation through the CLI can be done through Diskpart.
- **Diskpart** is a terminal-based tool built for managing disks right from the command line.
- To launch, open a command prompt, and run `Diskpart`
- This will open another terminal window, where the prompt reads `DISKPART>`
- You can list the current disks on the system by typing `list disk`


### Windows: Mounting and Unmounting a Filesystem

After you format a filesystem, you have to mount the filesystem to a new drive.

**Mounting** is making something accessible to the computer, like a filesystem or a hard disk.

Windows does this automatically. All you have to do is, when you're done using the drive, to safely eject (essentially, ummount) the drive.


### Linux: Disk Partitioning and Formatting a Filesystem

Linux has several partitioning command line tools; one that supports both MBR and GPT partitioning is the **Parted** tool. 

Parted can be used in two modes:
- Interactive, meaning we're launched into a separate program (like when we use the `less` command)
- Command line, meaning you just run commands while still in your shell.

To show what disks are connected to the computer, run `sudo parted -l`. This lists out the disks that are connected to our computer.
- The number field (in Parted) corresponds to the number of partitions on the disk. 
  - So the first partition will correspond to `/dev/sda1`, the second will be `/dev/sda2`, etc.
- The start field is where the partition starts on the disk.
  - For example, starting at 1,049 kilobytes and ending at 538 megabytes.
- The field after that shows how large the partition size is.
- The next field tells us what file system is on the partition.
- Then, the name.
- Finally, some flags that are associated with the partition.

The `mklabel` command sets a disk label to be recognized.

The `mkpart` command is used inside the Parted tool, and requires the following information:
- What type of partition you want to make;
- What file system you want to use;
- The start of the disk;
- And the end of the disk.

Partition type is only meaningful for MBR partition tables--remember that MBR uses primary, extended, and logical partitions.

Some operating systems measure one kilobyte as 1,024 bytes, even though that is actually a *kibibyte* and not a kilobyte. When dealing with data storage, you want to be as absolutely precise in measurement as you can be, so you don't waste precious memory space.

After this step, `quit` out of Parted, since you need to format the partition with the filesystem.
- Do this by running `sudo mkfs -t ext4 /dev/PARTITION`


### Linux: Mounting and Unmounting a Filesystem

To begin interacting with the disk, you need to mount the filesystem to the directory. But first, you need to create a directory on your computer, and then mount the filesystem to the directory.
- EX: `sudo mount /dev/sdb1 /my_usb/`

You can also unmount the filesystem using the `umount` command.
- When you shut down your computer, disks that were mounted manually are automatically unmounted.
- Always be sure to unmount a filesystem of a drive before physically disconnecting the drive.

You can permanently mount a disk if you need it to automatically load up when the computer boots.
- To do this, you need to modify a file called `/etc/fstab` ("filesystems table"). Inside, you'll see a list of unique device IDs, their mount points, what type of filesystem they are, and other information.
- The first field you'd need to add for `/etc/fstab` is the universally unique identifier (UUID) of the disk.
  - To get the UUID of your devices, you can run `sudo blkid`. 
  - This will show the UUID for block device IDs (aka storage device IDs).


### Windows: Swap

A relevant concept to disks and partitions is swap space. But before talking about swap space, let's review virtual memory.
- Recall that **virtual memory** is how our OS provides the physical memory available in our computers (like RAM) to the applications that run on the computer.
- It does so by creating a *mapping*, a virtual-to-physical address.
- This provides several benefits:
  - The program (which needs to access memory) doesn't have to worry about what portions of memory other programs might be using;
  - The program doesn't have to keep track fo where the data it's using is located in RAM;

Virtual memory also allows the computer to use more memory than it physically has installed.
- It does this by dedicating an are of the hard drive to use as a storage base, for blocks of data called *pages*.
- When a particular page of data isn't being used by an application, it gets evicted.
  - This means it gets copied out of memory, onto the hard drive.
  - This is because accessing data on RAM is much faster than the hard drive (where space is at a premium)
  - So, the operating system wants to keep the most commonly-accessed data pages in RAM;
  - And pages not used in a while are stored on the disk.
- A good analogy is that swap space is your pocket; and the hard drive is your backpack.

Windows provides a way to modify the size, number, and location fo paging files. This is done through the "System Properties" applet, in the Control Panel.


### Linux: Swap

In Linux, the dedicated area of the hard drive used for virtual memory is known as **swap space**.

- To make swap space, go into the Parted tool, and select where your storage device is.
- Partition it again, to make a swap partition.
- Then format the `linux-swap` filesystem on it.
- Swap isn't actually a filesystem, so it isn't done yet!
  - (Remember, pages go into swap, not file data.)
- Quit out of Parted, then run `sudo mkswap dev` with the location of the new swap partition.
- Lastly, run `sudo swapon` to the location, to enable swap on the device.

If you want to automatically mount swap space every time the computer boots up, just add a swap entry to the `/etc fstab` file.


### Windows: Files

Remember that the operating system manages file data, file metadata, and filesystems.
- When we talk about data, we're referring to the actual contents of the file (like a text document saved to hard drive).
- The file metadata includes everything else (like owner of the file, permissions, size of the file, location on hard drive, etc)

#### How does NTFS store and represent files?
- NTFS uses something called the **master file table (MFT)** to organize everything.
- Every file on a volume has at least one entry in the MFT (including the MFT itself)
  - Usually, there's a 1:1 correspondence between files and MFT records;
  - But if a file has many attributes, there might be more than one record to represent it.
  - Remember that attributes include file name, creation time stamp, its permission, compression, location, etc

When you create files on an NTFS filesystem, entries get added to the MFT.
- When files get deleted, their entries in the MFT are marked as *free* so they can get reused.

An important part of a file's entry in the MFT is an identifier called the **file record number**.
- This is the index of the file's entry in the MFT.
- A special type of file in Windows is called a *shortcut*
  - A shortcut is just another file and another entry in the MFT;
  - But it has a reference to some destination, so when run, it directs you to that destination.

Aside from creating shortcuts, NTFS provides two other ways to access other files, in hard and symbolic links.

**Symbolic links** are like shortcuts, but at the filesystem level.
- When you create a symbolic link, you create an entry in the MFT that points to the name of another entry/file.
- But unlike shortcuts, symbolic links are treated as substitutes for the file they're linked to in almost every meaningful way.

When you create a **hard link** in NTFS, an entry is added to the MFT that points to the linked file record number, not the name of the file.
- This means the file name of the target can change, and the hard link will still point to it.
- Since a hard link points out the file record number and not the file name, you can change the name of the original file and the link will still work.


### Linux: Files

In Linux, metadata and files are organized into a structure called an **inode**.
- Inodes are similar to the Windows NTFS MFT records.
- We store inodes in an inode table, and they help us manage the files on our file system.
- The inode itself doesn't actually store file date or file name; but it does store everything else about a file.

Shortcuts in Linux are referred to as **softlinks**, or **symlinks**. 
- They work in a similar way symbolic links work in Windows, in that they just point to another file.
- Softlinks allow us to link to another file using a file name;
- They're great for creating shortcuts to other files.
- To create a softlink, run the `ln` command with the `-s` flag for softlink.
  - So `ln -s FILENAME FILENAME_SOFTLINK`

The other type of links found in Linux are **hardlinks**.
- Similar to Windows, hardlinks don't point to a file;
- In Linux, they link to an inode, which is stored in an inode table on the file system.
- Essentially, when you creating a hardlink, you're pointing to a physical location on disk (more specifically, on the filesystem).
  - But if you deleted a file of a hardlink, all other hardlinks would still work.
- In the third field of file details, the field actually indicates the amount of hardlinks a file has.
  - When the hardlink count of a file reaches zero, then the file is completely removed from the computer.
- To create a hardlink, run the `ln` command to specify a hardlink.
  - So `ln FILENAME FILENAME_HARDLINK`

Hardlinks are great if you need to have the same file stored in different places, but you don't want to take up any additional space on the volume. (Better than softlinks, since those can be broken.)


### Windows: Disk Usage

To check disk usage, open up the Computer Management utility; then go to the Disk Management console; and right-click on the partition you're interested in and click "Properties."

The "Disk Cleanup" button will launch a program called `cleanmanager.exe`, which performs housekeeping tasks such as deleting temporary files, compressing old/rarely-used files, cleaning up logs, and emptying the recycle bin.

The command line disk usage utility can be useful for creating scripts (which may need text-based output instead of visual reports in the GUI).

Another task related to disk health is called **defragmentation**.
- The idea behind disk defragmentation is to take all the files stored on a given disk, and reorganize them into neighboring locations.
- Having files ordered like this will make it easier for hard drive disks, which use an actuator arm to write to and read from a spinning disk.
  - The head of the actuator arm will actually travel less to read the data it needs.
- This is less of a benefit for solid state drives, since there is no physical read/write head that moves around a spinning disk.
- Defragmentation is a regularly-scheduled task in Windows.
  - To manually defragment, open up the Disk Defragmenter tool bundled with Windows.

Instead, for SSD drives, the operating system can use a process called **trim** to reclaim unused portions of the solid state disk.


### Linux: Disk Usage

In Linux, you can view disk utilization on your computer with the `du -h` command.
- The `du`, or "disk usage" command, shows the disk usage of a specific directory.
  - If you don't specify a directory, it'll default to your current one.
- The `-h` flag gives you the data measurements in "human readable" form.
- You should use the `du` command if you want to know how much data space is being used by files in a directory.

Another command you can use if you want to know how much free space you have on your machine is the `df`, or "disk free" command.
- This shows you the free space available on your entire machine.
- Again, the `-h` flag presents you the data measurements in human readable form.
- You should use the `df` command if you want to know how much free space you have on your entire system.

Linux generally does a better job of avoiding fragmentation than Windows does.


### Windows: Filesystem Repair

When we read or write something to a drive, we actually put it into a buffer, or cache, first.
- A **data buffer** is a region of RAM that's used to temporarily store data while it's being moved around.
  - So when you copy something from your OS to your USB drive, it first gets copied to a data buffer because RAM operates faster than hard drives.

If you don't properly unmount a filesystem and give your buffer enough time to finish moving data, you run the risk of data corruption.

NTFS has several advanced features included to help minimize the danger of corruption (as well as try to recover damaged files).
- One such feature, through a process called *journaling*, logs changes made to a file's metadata into a log file, called the NTFS log.
  - By logging these changes, NTFS creates a history of the actions it's taken; meaning it can look at the log to see what the current state of the file system should be.
- In addition to journaling, NTFS implements *self-healing*.
  - This mechanism makes changes to minor problems and corruptions on the disk automatically in the background
  - It does this while Windows is running, so you don't need to perform a reboot.
- To check the status of the self-healing process, open an administrative command prompt;
  - Then run the `fsutil repair query DRIVE`

### Linux: Filesystem Repair

To repair a filesystem manually in Linux, you can use `fsck`, the file system check command.
- Ex:`sudo fsck /dev/sdb`

*Don't run* `fsck` *on a mounted partition*, as there's a high chance it will damage the filesystem.

[Content](#content)

------------------------------------------------------------------------------------------------------------Process Management------------------------------------------------------------------------

# Process Management

## Life of a Process

### Programs vs Processes Revisited

Recall that **programs** are applications we can run (like Chrome); and that **processes** are programs that are running.

- When we launch a process, we're executing a program.
- When processes are run, they take up hardware resources like CPU and RAM

#### How processes work
- When you open up an application like a word processor, you're launching a process.
- That process gets assigned something called a **process ID** to uniquely identify it from other processes.
- The computer sees that the process needs hardware resources to run;
  - So the kernel makes decisions to figure out what resources to give it.

Besides visible processes, there are also **background processes**, also known as *daemon processes*.
- Background processes are processes that run in the background.
- We rarely see them, and rarely interact with them; but the system needs them to function.
  - They include processes like scheduling resources, logging, managing networks, and more.


### Windows: Process Creation and Termination

When Windows boots up, the first non-kernel user mode that starts is the Session Manager Subsystem, or `smss.exe`. This is the process in charge of setting the scene for the OS to work.
- It then kicks off the login process, called `winlogon.exe`
- It also starts the Client/Server Runtime Subsystem (`csrss.exe`), which handles running the Windows GUI and command line console.

Linux uses a process called `init`, but this is not equivalent to `smss.exe`.

In Windows, each new process created needs a parent to tell the operating system that a new process needs to be made. The child process inherits some things like variables and settings, which we collectively refer to as an **environment**.
- Unlike in Linux, Windows processes can operate independently of their parents.
- You can use a command prompt to stop processes via the `taskkill` utility.
  - A common way of using this utility is with an identification number, known as the **process ID (PID)** to tell task kill which process you'd like stopped.
  - Ex: `taskkill /pid PROCESSID


### Linux: Process Creation and Termination

- Linux processes have parent-child relationships.
  - This means that every process you launch comes from another command.
- Logically, if all processes come from another process, there must be an initial process that starts it all.
  - This is **init**
  - When you start up your computer, the kernel creates a process called `init`, which has a PID of `. 
  - `init` starts up other processes that we need to get our computer up and running.
- When processes complete their tasks, they'll generally terminate automatically.
- Once a process terminates, it will release all the resources it was using back to the kernel, so they can be used for another process.


## Managing Processes

### Windows: Reading Process Information

You can think of processes as programs in motion. There are different ways you can investigate which processes are running on a Windows computer, and more methods of interacting with them.

In Windows, the **Task Manager**, or `taskmgr.exe` is one way of obtaining process information. 
- You can open it with `Ctrl` + `Shift` + `Esc` key combination; or locate it through the Start Menu.
  - If you click on the processes tab, you can see a list of processes the current user is running; along with system-level processes the user can see.
  - The task manager tells you what app or image the process is running, along with the user who launched it, and the CPU or memory resources it's using.
- To kill a process, you can select any of the process rows and click the "End Task" button.

#### Obtaining Process ID
- While in task manager, you can click on the details menu option
  - Among the information displayed is the PID
- You can also see this information from both the command prompt and PowerShell:
  - In the command prompt, use the `tasklist` command to show all the running processes.
  - In PowerShell, you can use the cmdlet called `Get-Process` to do the same.


### Linux: Reading Process Information

To view the processes running on a Linux system, run the `ps -x` command. This shows you a snapshot of the current processes you have running.

From left to right:
- The PID is the process ID
- TTY is the terminal associated with the process
- STAT is the process status; 
  - An R here means the process is running, or waiting to run
  - A T is for stopped, meaning a process has been suspended
  - S is for interruptible sleep, meaning the task is waiting for an event to complete before it resumes
- TIME is the total CPU time the process has taken up
- And CMD is the name of the command that we're running

Another way to view process information is to view their corresponding files, in the `/proc` directory.
The `/proc` directory is not very practical when you need to troubleshoot issues with processes.


### Windows: Signals

- To tell a process to quit at the system level, we use something called a signal. 
- A **signal** is a way to tell a process that something's just happened.
- You can generate a signal with special characters on your keyboard, and through other processes and software.
  - One of the most common signals you'll come across is SIGINT, which stands for "signal interrupt"
  - You can send this signal to a running process with the `CTRL` + `C` key combination.


### Linux: Signals

Much like in Windows, the signal interrupt (SIGINT) process can be run by `CTRL` + `C`


### Windows: Managing Processes

**Process Explorer** is a utility Microsoft created to let IT support specialists, system administrators, and other users look at running processes.
- It doesn't come with Windows, and you need to download it from Microsoft's website.
- Process Explorer presents a view of the current/active processes in the top window pane.
  - You can also see a list of files a selected process is using in the bottom window pane.
  - **MUI** stands for **multilingual user interface**, and contains a package of features to support different languages.
- A nested process indicates that it's a child process.
- Right-click will present several options, including Kill Process, Kill Process Tree, Restart, or Suspend.
- If you restart a process using the Process Explorer utility, the new parent of that process will be Process Explorer itself (since it launched it)

In summary, the Task Manager, the command prompt's tasklist utility, and the `Get-Process` commndlet from PowerShell all help you gather information about processes running on Windows OS.


### Linux: Managing Processes

#### SIGTERM
- We can terminate a process using the `kill` command
  - A `kill` command without any flags sends a termination signal, or SIGTERM
  - This will kill the process; but gives it some time to clean up the resources it was using
  - If you don't give the process a chance to clean up, it could cause file corruption

#### SIGKILL
- This signal does its very best to make sure your process absolutely gets terminated, without giving it time to clean up
- To send a SIGKILL signal, you add a flag to the kill command: `kill -KILL [process]`
- This should be a last resort for process termination
  - Since it doesn't do any cleanup, you could do more harm than good to your files

#### SIGTSTOP
- If you want to pause a process instead of terminating it, you can do this with the SIGTSTP signal
  - This means "terminal stop," which puts your process in a suspended state
- Run `kill -TSTP` to achieve this
  - The keyboard combination `Ctrl` + `Z` also achieves this
- To resume the execution of the process, the **SIGCONT** ("continue signal") can be run:
  - `kill -CONT`


### Mobile App Management

[ Take notes ]

Rather than view the list of running processes, mobile operating systems (like iOS and Android) let you manage mobile apps that are running on the OS.

- Both iOS and Android let you open the App Switcher, where you see a list of apps running on the OS.
- The app you're using is called the *foreground app*
- The other apps are called *background apps*
- Background apps are suspended -- paused, but not closed
- The App Switcher enables you to swipe up to close background apps


## Process Utilization

### Windows: Resource Monitoring

In Windows, one of the most common ways to take a peek at how the system resources are doing, is by using the **Resource Monitoring** tool. You can run it from the Start menu.

Another method is to use PowerShell, specifically `Get-Process`. Sorting and selecting a search through `Get-Process` is a helpful way to filter down to just the data you need.


### Linux: Resource Monitoring

#### top
- A useful command to find out what your system utilization looks like in real time, is the `top` command.
- `top` shows us the top processes that are using the most resources on our machine.
  - We can also get a quick snapshot of total tasks running or idle, CPU usage, memory usage, and more.
  - "Percentage CPU" and "percentage mem" show what CPU and memory usage a single task is taking up
- To exit the top command mode, hit the `Q` key ("quit")
- If you find that top shows a certain task is taking up a lot of memory or CPU, you can investigate what the process is doing (terminating if necessary)

#### uptime
- Another useful tool for resource utilization is the `uptime` command
- This command shows information about the current time, how long your system's been running, how many users are logged on, and what the load average of your machine is
  - Load averages are useful when you need to see how your machine is doing over a certain period of time
  - In uptime, you can show the average CPU load in 1, 5, and 15-minute intervals

#### lsof
- The `lsof` command lists open files and what processes are using them.
- This command is useful for tracking down processes that are holding open files

[Content](#content)


-------------------------------------------------------------------------------------------------------Operating Systems in Practice-----------------------------------------------------------------


# Operating Systems in Practice

So far, you've learned:
- How to navigate Windows and Linux
- How to set up and manage users
- How to manage software
- How to work with disks and file systems
- How to work with processes and hardware resources

## Remote Access

### Remote Connection and SSH

[insert notes from course 1]

### Remote Connections on Windows

[insert notes from course 1]

### Remote Connection File Transfer

- **Secure copy (SCP)** is a command you can use in Linux to copy files between computers on a network.
  - It uses SSH to transfer the data
- To do this, run the `scp` command with a few flags:
  - `scp /home/user/file.txt user@IPADDRESS`

### Remote Connection File Transfer on Windows

- PuTTY supports the SCP protocol, and enables Windows computers to share files and data over a network.
- PuTTY comes with a tool called the **PuTTY Secure Copy Client**, or `pscp.exe`; it can be used to copy files similar to how the Linux SCP command works.
- Windows also uses shared to transfer files to multiple machines
  - Shared folders allow you to let other people access folders and files
  - Right-click on a folder you want to share; go over the "Share with" option; and from there, add users or groups to share the folder with.
  - To access it from other computers, open up "This PC"; go into the "Computer" tab; and you can map the folder directly to your computer with the "Map Network Drive" option
- You can share files via the `net share` command
  - It allows you do to the same thing as the GUI sharing-workflow, and you'll need to specify what kind of permissions to give users.

## Virtualization

### Virtual Machines

A **virtual instance** is a single virtual machine.


## Logging

### System Monitoring

- Recall that a log is like a computer's diary -- it records events that happen on your system.
- Logs tell us important things like errors that occurred, changes that were made, etc, and are a reliable source of information.
- The act of creating log events is called **logging**.

### The Windows Event Viewer

- In Windows, events logged by the operating system are stored in an application called the *Event Viewer*.
- You can launch the Event Viewer from the Start Menu, or by typing in `eventvwr.msc` from the run box.
- Custom Views allow you to create filters that look across all event logs, and tease out just the information you're interested in.


### Linux Logs

- Logs in Linux are stored in the `/var/log` directory
  - Recall that `/var` stands for "variable," meaning files that constantly change are kept in this directory -- and logs are constantly changing.
- `/var/log/auth.log` logs authorization and security-related events
- `/var/log/kern.log` logs kernal messages
- `/var/log/dmesg` logs system startup messages
- The one log file that logs pretty much everything on your system is the `/var/log/syslog` file
  - The only thing it doesn't log by default are off events
  - When troubleshooting issues with user machines, this directory will usually contain the most comprehensive information about your system, and should be your first stop
- Log systems do a generally good job of cleaning out log files to make room for new ones
  - This is accomplished through what's called log rotation
  - In Linux, the utility to rotate logs is called `logrotate`

#### Reading a log file

- The first field is the time stamp
  - Time stamps can appear in [Unix/epoch time]()
- The next field is the host name of the machine the event occurred on
- Next is the service that the log event is referring to
- Finally, the event that occurred


### Working with Logs

- To look at the logs in real time, you can use the `tail` command
  - Ex: `tail -f /var/log/syslog` (`-f` option for "file")


## Operating System Deployment

### Imaging Software

- Recall that to **image** a machine, is to format a machine with an image of another machine.
- This includes everything, from the operating system to the settings.
- In the IT world, installing an operating system for a fleet of computers can be made easier through tools designed to image computers.

### Operating Systems Deployment Methods

One tool we can use to image computers is a *disk cloning tool*.
- It makes a copy of an entire disk, and allows you to back up a current machine or set up a new one
- The benefit of disk cloning over a standalone installation media is that you can also install settings and folders that you might need.

An option in disk-to-disk cloning is where you connect an external hard drive to the machine you want to clone. You can connect a hard drive like your HDD or SSD into something known as an *external hard drive dock*. Then you can use any disk cloning tool of your choice.

In Linux, `dd` is a command to copy files, that's also able to clone a drive (since everything in Linux is a file).


### Mobile Device Resetting and Imaging

Mobile devices are installed with an operating system at the factory; so a **factory reset** reverts the device back to the state it was in when the device was shipped from the factory.

- Doing a factory reset while expansion storage is attached might erase data that you want to keep;
- Likewise, factory reset for many devices may leave the contents of expansion storage intact
  - You don't want to re-purpose or decommission a device with personal or proprietary information still attached.

Over time, mobile device manufacturers will release updates to the device operating system. These updates will usually be delivered *over the air*, or OTA. An OTA update is one that's downloaded and installed by the mobile device itself.

There are times when you might need to use a computer to install operating system updates. Here, you would download the update to a computer; attach the mobile device to the computer via a USB cable; and run some software on the computer that will *re-flash* the mobile device.

[Content](#content)