# 🐧 Linux Fundamentals – Complete Notes

> **Source:** TryHackMe – Linux Fundamentals (Parts 1, 2 & 3)  
> **Topics:** Commands, File System, Permissions, Processes, Automation

---

## 📌 Table of Contents

- [Part 1 – Background & Basic Commands](#part-1)
- [Part 2 – SSH, Flags, Filesystem Interaction, Permissions](#part-2)
- [Part 3 – Text Editors, Utilities, Processes, Automation](#part-3)

---

<a name="part-1"></a>
# 🗂️ Part 1 – Linux Background & Basic Commands

## Where is Linux Used?

Linux is considerably more lightweight than other Operating Systems (OSs) such as Windows. You've likely used Linux in some form or another every day. Linux powers things such as:

- Websites that you visit
- Car entertainment / control panels
- Point of Sale (PoS) systems such as checkout tills and registers in shops
- Critical infrastructure such as traffic light controllers or industrial sensors

Linux comes in all shapes and sizes — suited best for what the system is being used for.

> **Examples:** Ubuntu and Debian are some of the more commonplace distributions of Linux because they are so extensible — i.e., you can run Ubuntu as a server.

> 📝 **NOTE:** Ubuntu Server can run on systems with only **512 MB of RAM!**

> 📅 **1991** was the year the first release of a Linux Operating System happened.

---

## 💻 Few Commands

A large part of interacting with these systems is using the **"Terminal"**.

| Command | Description |
|---------|-------------|
| `echo` | Output any text that we provide |
| `whoami` | Find out what user we are currently logged in as |

### Examples

```bash
tryhackme@linux1:~$ echo Hello
Hello

tryhackme@linux1:~$ echo "Hello friend!"
Hello friend!
```

> 💡 If we want to `echo` a single word, we don't need to use double quotes. However, the string should be enclosed within double quotes if one or more spaces are present. e.g., `echo "Hello friend!"`

```bash
tryhackme@linux1:~$ whoami
```

---

## 📁 Interacting with the File System

| Command | Full Name |
|---------|-----------|
| `ls` | Listing |
| `cd` | Change Directory |
| `cat` | Concatenate |
| `pwd` | Print Working Directory |

---

### `ls` – Listing Files in Our Current Directory

Before we can do anything such as finding out the contents of any files or folders, we need to know what exists in the first place. This can be done using the `ls` command (short for listing).

```bash
tryhackme@linux1:~$ ls
'Important Files'  'My Documents'  Notes  Pictures
```

> 💡 **Tip!** We can list the contents of a directory without having to navigate to it by using `ls` and the name of the directory. i.e., `ls Pictures`

---

### `cd` – Changing Our Current Directory

Now that we know that folders exist, we need to use the `cd` command to change to that directory. Say if we wanted to open the "Pictures" directory — we do `cd Pictures`. Where again, we want to find out the contents of this "Pictures" directory, we'd use `ls` again.

```bash
tryhackme@linux1:~$ cd Pictures
tryhackme@linux1:~/Pictures$ ls
dog-picture1.jpg
```

---

### `cat` – Outputting the Contents of a File

`cat` is short for **concatenating** and is a fantastic way to output the contents of files (not just text files).

```bash
tryhackme@linux1:~$ cd Documents
tryhackme@linux1:~/Documents$ ls
todo.txt
tryhackme@linux1:~/Documents$ cat todo.txt
Here's something important
```

> ✅ We can use `cat` to output the contents of a file within directories without having to navigate to it, by using `cat` and the name of the directory:
> ```bash
> cat /home/ubuntu/Documents/todo.txt
> ```

---

### `pwd` – Finding Out the Full Path to Our Current Working Directory

It's easy to lose track of where we are exactly on the filesystem, which is why `pwd` (print working directory) is useful.

```bash
tryhackme@linux1:~/Documents$ pwd
/home/ubuntu/Documents
```

---

## 🔍 Searching for Files

### Using `find`

The `find` command is fantastic in the sense that it can be used both very simply or rather complex depending upon what it is you want to do exactly.

```bash
tryhackme@linux1:~$ ls
Desktop  Documents  Pictures  folder1
```

#### Find by Name
```bash
tryhackme@linux1:~$ find -name passwords.txt
./folder1/passwords.txt
```

#### Find by Extension (Wildcard)
```bash
tryhackme@linux1:~$ find -name *.txt
./folder1/passwords.txt
./Documents/todo.txt
```

`find` has managed to find:
1. `passwords.txt` located within "folder1"
2. `todo.txt` located within "Documents"

---

### Using `grep`

The `grep` command allows us to search the contents of files for specific values that we are looking for.

#### Count entries with `wc`
```bash
tryhackme@linux1:~$ wc -l access.log
244 access.log
```

#### Search file contents
```bash
tryhackme@linux1:~$ grep "81.143.211.90" access.log
81.143.211.90 - - [25/Mar/2021:11:17 + 0000] "GET /HTTP/1.1" 200 417 "-" "Mozilla/5.0 (Linux; Android 7.0; Moto G(4))"
```

---

### Searching Recursively with `grep`

Sometimes the information we are looking for is spread across multiple files inside a directory. Instead of checking each file individually, we can tell `grep` to search recursively through all files and subdirectories.

To do this, we use the **-R (recursive)** option:

```bash
grep -R "PRETTY_NAME" /etc/
```

This will:
- Search every file in the current directory
- Search all subdirectories
- Show where `PRETTY_NAME` appears

**Example Output:**
```
grep: /etc/sudoers: Permission denied
/etc/os-release: PRETTY_NAME="Ubuntu"
```

---

## ⚙️ An Introduction to Shell Operators

| Symbol/Operator | Description |
|-----------------|-------------|
| `&` | Allows you to run commands in the background of your terminal |
| `&&` | Allows you to combine multiple commands together in one line of your terminal |
| `>` | A redirector — take the output from a command and direct it elsewhere |
| `>>` | Does the same function as `>` but appends the output rather than replacing |

---

### Operator `&`

This operator allows us to execute commands in the background. For example, if we want to copy a large file, this will obviously take quite a long time and will leave us unable to do anything else until the file successfully copies. The `&` shell operator allows us to execute a command and have it run in the background, allowing us to do other things!

---

### Operator `&&`

This shell operator is a bit misleading in the sense of how familiar it is to its partner `&`. Unlike the `&` operator, we can use `&&` to make a list of commands to run, for example `command1 && command2`. However, it's worth noting that `command2` will only run if `command1` was successful.

---

### Operator `>`

This operator is what's known as an **output redirector**. What this essentially means is that we take the output from a command we run and send that output to somewhere else.

Let's say we wanted to create a file named "welcome" with the message "hey". We can run `echo hey > welcome` where we want the file created with the contents "hey":

```bash
tryhackme@linux1:~$ echo Hey > welcome
tryhackme@linux1:~$ cat welcome
Hey
```

---

### Operator `>>`

What makes this operator different is that rather than overwriting any contents within a file, it instead just puts the output at the end. The `>>` operator allows us to append the output to the bottom of the file rather than replacing the contents:

```bash
tryhackme@linux1:~$ echo hello >> welcome
tryhackme@linux1:~$ cat welcome
Hey
hello
```

---

<a name="part-2"></a>
# 🔐 Part 2 – SSH, Flags, Permissions & Filesystem

## Accessing Linux Machine Using SSH (Deploy)

The protocol used is called **Secure Shell** or **SSH** for short and is the common means of connecting to and interacting with the command line of a remote Linux machine.

### What is SSH & How Does it Work?

Secure Shell or SSH is simply a protocol between devices in an encrypted form. Using cryptography, any input we send in a human-readable format is encrypted for travelling over a network — where it is then unencrypted once it reaches the remote machine.

```
Computer  ──── The Internet ────  Linux Server
             f6b97e4f49aca8a5
Hello World                       Hello World
```

- SSH allows us to remotely execute commands on another device remotely.

> 📝 **NOTE:** When we type a password in SSH login prompt, there is no visible feedback — you will **not** be able to see any text or symbols appear as you type the password.

---

## Introduction to Flags and Switches

A majority of commands allow for **arguments** to be provided. These arguments are identified by a hyphen and a certain keyword known as **flags** or **switches**.

For example, `ls` lists the contents of the working directory. However, hidden files are not shown. We can use flags and switches to extend the behaviour of commands.

```bash
tryhackme@linux2:~$ ls
folder1
```

After using the `-a` argument (short for `--all`), we now suddenly have an output with a few more files and folders such as `.hidden_folder`. Files and folders with `.` are hidden files.

```bash
tryhackme@linux2:~$ ls -a
.hidden_folder  folder1
```

Commands that accept these will also have a `--help` option. This option will list the possible options that the command accepts, provide a brief description and example of how to use it.

---

### The Man(ual) Page

The manual pages are a great source of information for both system commands and applications available on both a Linux machine, which is accessible on the machine itself and online.

To access this documentation, we can use the `man` command and then provide the command we want to read the documentation for:

```bash
man ls
```

---

## Filesystem Interaction

In this task, we're going to learn some more commands for interacting with the file system to allow us to:

- Create files and folders
- Move files and folders
- Delete files and folders

| Command | Full Name | Purpose |
|---------|-----------|---------|
| `touch` | touch | Create file |
| `mkdir` | make directory | Create a folder |
| `cp` | copy | Copy a file or folder |
| `mv` | move | Move a file or folder |
| `rm` | remove | Remove a file or folder |
| `file` | file | Determine the type of a file |

---

### Creating Files and Folders (`touch`, `mkdir`)

Creating files and folders on Linux is a simple process. The `touch` command takes exactly one argument — the name we want to give the file we create.

```bash
tryhackme@linux2:~$ touch note
tryhackme@linux2:~$ ls
folder1  note
```

This is a similar process for making a folder, using `mkdir`:

```bash
tryhackme@linux2:~$ mkdir mydirectory
tryhackme@linux2:~$ ls
folder1  mydirectory  note
```

---

### Removing Files and Folders (`rm`)

`rm` is extraordinary out of the commands that we've covered so far. You can simply remove files by using `rm`. However, we need to provide the `-R` switch alongside the name of the directory you wish to remove.

```bash
# Remove a file
tryhackme@linux2:~$ rm note
tryhackme@linux2:~$ ls
folder1  mydirectory

# Remove a directory recursively
tryhackme@linux2:~$ rm -R mydirectory
tryhackme@linux2:~$ ls
folder1
```

---

### Copying and Moving Files and Folders (`cp`, `mv`)

Copying and moving files is an important functionality on a Linux machine. Starting with `cp`, this command takes two arguments:
1. The name of the existing file
2. The name we wish to assign to the new file when copying

`cp` copies the entire contents of the existing file into the new file.

```bash
tryhackme@linux2:~$ cp note note2
tryhackme@linux2:~$ ls
folder1  note  note2
```

Moving a file takes two arguments, just like the `cp` command. Not only can we use `mv` to move a file to a new folder, but we can also use `mv` to rename a file or folder.

```bash
tryhackme@linux2:~$ mv note2 note3
tryhackme@linux2:~$ ls
folder1  note  note3
```

---

### Determining File Type (`file`)

Files usually have what's known as an extension to make this easier. For example, text files usually have an extension of `.txt`. But this is not necessary.

Enter the `file` command. This command takes one argument. For example, we'll use `file` to confirm whether or not the "note" file in our examples is indeed a text file:

```bash
tryhackme@linux2:~$ file note
note: ASCII text
```

---

## Permissions 101

As we would have already found out by now, certain users cannot access certain files or folders.

For example, the `ls` command, which lists the contents of the current directory. When using the `-l` switch, we can see ten columns. However, we're only interested in the first three columns.

```bash
tryhackme@linux2:~$ ls -lh
-rw-r--r-- 1 cmnatic cmnatic  8 Feb 19 10:37 file1
-rw-r--r-- 8 cmnatic cmnatic    Feb 19 10:37 file2
```

These three columns are very important in determining certain characteristics of a file or folder. A file or folder can have a couple of characteristics that determine both what actions are allowed and what user or group has the ability to perform the given action — such as the following:

- **Read**
- **Write**
- **Execute**

---

### Briefly: The Difference Between Users & Groups

The great thing about Linux is that permissions can be so granular, that whilst a user technically owns a file, if the permissions have been set, then a group of users can also have either the same or a different set of permissions to the exact same file without affecting the file owner itself.

---

### Switching Between Users

Switching between users on a Linux install is easy work thanks to the `su` command. Unless you are the root user (or using root permissions through `sudo`), then you are required to know two things to facilitate this transition of user accounts:
- The user we wish to switch to
- The user's password

---

## Understanding File Permissions in Numeric Format

In Linux, every file and directory has a set of permissions that control who can read, write or execute it. These permissions are often displayed in **symbolic format**, such as: `rwxrwxrwx`

This format is split into three groups:

| Section | Applies To | Example |
|---------|-----------|---------|
| First 3 | Owner | rwx |
| Next 3 | Group | rwx |
| Last 3 | Others | rwx |

Each letter represents a specific permission:
- `r` = read
- `w` = write
- `x` = execute

### Converting Symbolic Permissions to Numbers

Each permission has a numeric value:

| Permission | Value |
|------------|-------|
| Read (r) | 4 |
| Write (w) | 2 |
| Execute (x) | 1 |

To calculate the numeric value, we add the values together for each group.

**Example:** `rwxrwxrwx`

| Group | Permissions | Calculation | Value |
|-------|-------------|-------------|-------|
| Owner | rwx | 4+2+1 | 7 |
| Group | rwx | 4+2+1 | 7 |
| Others | rwx | 4+2+1 | 7 |

```
rwxrwxrwx = 777
```

---

## Common Directories

### `/etc`
This root directory is one of the most important root directories on your system. The `etc` folder (short for **etcetera**) is a common-place location to store system files that are used by your operating system.

### `/var`
The `/var` directory, with "var" being short for **variable data**, is one of the main root folders found on a Linux install. This folder stores data that is frequently accessed or written by services or applications running on the system.

### `/root`
Unlike the `/home` directory, the `/root` folder is actually the home for the "root" system user. There isn't anything more to this folder other than just understanding that this is the home directory for the "root" user.

### `/tmp`
This is a unique root directory found on a Linux install. Short for **"temporary"**. The `/tmp` directory is volatile and is used to store data that is only needed to be accessed once or twice.

---

<a name="part-3"></a>
# ✏️ Part 3 – Text Editors, Utilities, Processes & Automation

## Terminal Text Editors

### Nano

It is easy to get started with Nano! To create or edit a file using nano, we simply use `nano filename` — replacing "filename" with the name of the file you wish to edit.

Once we press enter to execute the command, nano will launch where we can just begin to start entering or modifying our text. We can navigate each line using the "up" and "down" arrow keys or start a new line using the "Enter" key on your keyboard.

Nano has a few features that are easy to remember & cover the most general things you would want out of a text editor including:
- Searching for text
- Copying and pasting
- Jumping to a line number
- Finding out what line number you are on

We can use these features of nano by pressing the **`Ctrl`** key (which is represented as `^` on Linux) and a corresponding letter.

---

### VIM

VIM is a much more advanced text editor. Some of VIM's benefits:

- **Customisable** — you can modify the keyboard shortcuts to be of your choosing.
- **Syntax Highlighting** — this is useful if you are writing or maintaining code, making it a popular choice for software developers.
- VIM works on all terminals where nano may not be installed.

---

## General/Useful Utilities

### Downloading Files (`wget`)

This command allows us to download files from the web via HTTP — as if we were accessing the file in our browser. We simply need to provide the address of the resource that we wish to download.

For example, if I wanted to download a file named "myfile.txt" onto my machine, assuming I know the web address it — it would look something like this:

```bash
wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt
```

---

### Transferring Files from Your Host – SCP (SSH)

**Secure copy**, or **SCP**, is just that — a means of securely copying files. Unlike the regular `cp` command, this command allows us to transfer files between two computers using the SSH protocol to provide both authentication and encryption.

Working on a model of SOURCE and DESTINATION, SCP allows us to:
- Copy files and directories from our current system to a remote system
- Copy files and directories from a remote system to our current system

#### Copying TO a remote machine:

| Variable | Value |
|----------|-------|
| IP address of remote system | 192.168.1.30 |
| User on the remote system | ubuntu |
| Name of the file on the local system | important.txt |
| Name to store the file as on remote | transferred.txt |

```bash
scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt
```

#### Copying FROM a remote machine:

| Variable | Value |
|----------|-------|
| IP address of remote system | 192.168.1.30 |
| User on the remote system | ubuntu |
| Name of the file on remote system | documents.txt |
| Name to store the file as on our system | notes.txt |

```bash
scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt
```

---

## Processes 101

Processes are the programs that are running on our machines. They are managed by the **kernel**, where each process will have an ID associated with it, also known as its **PID**. The PID increments for the order in which the process starts — i.e., the 60th process will have a PID of 60.

### Viewing Processes

We can use the friendly `ps` command to provide a list of the running processes as our user's session and some additional information such as its status code, the session that is running it, how much usage time of the CPU it is using, and the name of the actual program or command that is being executed.

To see the processes run by other users and those that don't run from a session (i.e., system processes), we need to provide `aux` to the `ps` command like so:

```bash
ps aux
```

Another very useful command is the `top` command! `top` gives us real-time statistics about the processes running on your system instead of a one-time view. These statistics will refresh every 10 seconds, but will also refresh when we use the arrow key to browse the various rows.

---

### Managing Processes

We can send signals that terminate processes; there are a variety of types of signals that correlate to exactly how "cleanly" the processes are dealt with by the kerne
