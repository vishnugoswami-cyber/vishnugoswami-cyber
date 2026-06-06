# Module 5: Operating System Basics

---

## The Invisible Manager

An operating system (OS) is the core software that coordinates everything happening on a computer. It sits between the user, applications, and the system's physical hardware, acting as the invisible manager that keeps the entire machine running as one unified system.

```
User
  ↓
Applications
  ↓
Operating System
  ↓
Hardware
```

We need an operating system because it provides this all-important job of coordination and structuring that makes modern computing possible.

- **Kernel Space** – The privileged, locked-down core of the OS. This is where the kernel, the part of the operating system that directly manages hardware and system resources, runs.
- **User Space** – Where all standard applications run.

---

## Operating System Duties

Every OS is responsible for a few core duties that allow your computer to run safely, efficiently, and predictably.

### OS Responsibilities

- **Process Management** – Creates, schedules, prioritizes, and terminates running programs. The OS decides how much CPU time each process gets, making multitasking feel seamless.
  - *Ex:* Opening multiple apps like your browser, music player, and social media without your computer freezing.

- **Memory Management** – Allocates RAM to processes, protects each app's memory from other processes, and reclaims memory when apps are closed.
  - *Ex:* Opening multiple apps at once, the OS allocates RAM to each one and keeps them isolated so they don't interfere or crash each other.

- **File Management** – Organises files into directories, handles naming, paths, permissions, metadata (name, size, type, timestamps).
  - *Ex:* Creating a new folder, saving a photo, or setting a file to "read only".

- **User Management** – Handles multiple user accounts, authentication, and permissions to determine who can access what.
  - *Ex:* Logging in with your password and keeping your files inaccessible to other user accounts.

- **Device Management** – Loads drivers and provides a universal interface (hardware abstraction layer), so apps can say "print this" or "play this sound".
  - *Ex:* Plugging in a new mouse, printer, or external hard drive and having it work immediately.

---

## Operating System Security

It is important to understand that every OS also acts as a security foundation.

At a basic level, your operating system handles:

- **Authentication** – Verifies who you are through login passwords and biometrics.
- **Permissions** – Controls exactly what each user and app is allowed to read, write, or execute.
- **Isolation** – Keeps every process in its own protected box (kernel/user space separation).
- **System Protection** – Safeguards critical system files and settings from unauthorised changes.

---

## OS Interfaces

Interaction with the OS can be divided into two main parts: the **Graphical User Interface (GUI)** and the **Command-Line Interface (CLI)**.

### Graphical User Interface (GUI)
It provides a graphical representation of all the information you want to access on your computer. Think of folder icons, windows for your applications, and menus for settings.

### Command-Line Interface (CLI)
The CLI is where you enter specific text-based commands to retrieve or manipulate information. Instead of clicking on icons, you tell the computer exactly what you want using words and syntax that the system understands.

---

## The Operating System Landscape

Different devices and goals demand different designs, ranging from your phone to a web server in a data centre.

| OS Type | Primary Use | Key Characteristics |
|---|---|---|
| **Desktop** | Personal computers, daily work, gaming, content creation | Rich graphic interface, runs many apps at once, user-focused |
| **Server** | Web hosting, databases, cloud services, back-end | Headless (no GUI), maximum uptime, multi-user, handles concurrent access |
| **Mobile** | Smartphones and tablets | Touch-based UI, power efficient, always connected app sandboxing |
| **Embedded** | Appliances, cars, IoT devices, smart TVs, routers | Tiny footprint, runs on limited hardware, lightweight, scalable, rapid deployment |

### Real World Operating Systems

1. **Desktop** – Windows, macOS, Linux
2. **Server** – Windows Server, Linux, Unix
3. **Mobile** – Android, iOS
4. **Embedded and IoT Devices** – Embedded Linux, Real-Time OS
5. **Netflix** – Cloud/VMs, Containers – ephemeral

---

## Windows Basics

Early computers ran MS-DOS, which allowed a black screen where you had to type commands instead of clicking icons.

### Logging In and Authentication

The authentication process verifies your identity and determines the actions you're allowed to take once logged in.

Windows commonly uses the following account types:

- **Guest** – A restricted account intended for temporary access, with minimal permissions and no ability to change system settings.
- **Standard** – A user account for everyday tasks, such as running applications and changing personal settings, without access to system-wide changes.
- **Administrator** – A privileged account with full control over the system including software installation, configuration changes, and user management.

When we log in, we are presented with two main areas:
- **Desktop** – The main workspace where files, folders, and shortcuts live.
- **Taskbar** – A control strip that provides access to applications, system tools, settings, and notifications.

### Core Components and Concepts of Windows Server

1. Desktop Icons
2. Start Menu
3. Search
4. Task View
5. Pinned Applications and Folders
6. Network and Audio Settings
7. Date and Time
8. Notifications

---

## Configuring and Securing Windows

Keeping your operating system and applications up to date is an important part of maintaining a secure and stable system.

- Windows Settings and the Control Panel enable you to view and modify how your Windows system operates.

### The Task Manager

Task Manager is a built-in Windows tool that allows you to monitor what is happening on your system in real time.

Task Manager has five tabs to help you keep track of your systems:

1. Processes
2. Performance
3. Users
4. Details
5. Services

### Native Windows Security

Windows offers built-in security tools designed to help protect your system from threats such as malware, insecure applications, and unauthorised network access.

The Windows Security application is your central dashboard for managing Windows built-in protection measures. It is divided into four main sections:

- Virus and threat protection
- Firewall and network protection
- App and browser control
- Device security

### Windows Defender Firewall

Windows Defender Firewall is a built-in firewall designed to help protect your computer from unauthorised network traffic.

- **Domain** – Used when a system is connected to an organisation's domain network.
- **Private** – Intended for trusted networks, such as a home or lab environment.
- **Public** – Used for untrusted networks, such as public Wi-Fi.

---

## Linux CLI Basics

In cybersecurity, Linux is everywhere, powering servers, security tools, and even hacking environments.

The **Terminal** is a text-based interface for controlling a Linux system. Cybersecurity professionals use it because:
- It's faster than clicking around
- It gives more control
- Many security tools only run in the terminal

### ① "Where Am I?"

When you first open a terminal, you might not know what part of the system you're in. Use this command to find out: `pwd`

It stands for "print working directory", which basically means "show me the folder I'm currently in".

### ② "What's Around Me?"

Let's see what files and folders are here: `ls`

If we need more details, we can try: `ls -l`
It displays important information about the files and directories like file sizes, permissions, dates, and more.

#### Hidden Files

In order to get hidden files in the directory, we can append the command `ls -al`, and it will display all the hidden files present in the directory.

Hidden files aren't really *secret* — they start with a dot `.`, and Linux hides such files by default.

### ③ Let's Move Around

To walk through the file system, we can use: `cd <directory>`
For example: `cd Documents` — this will change our directory to Documents.
To go "back" one level, we will use the command `cd ..`

### ④ Learn the Power of "Find"

As the name suggests, this built-in utility is used to locate files within the file system. Here's a simple version of the command:
`find <starting-point> -name <filename>`

Begin the home directory symbol: `~`
So we will run the command: `find ~ -name mission_brief.txt`

### ⑤ Read the File

Another useful utility is `cat`. This is used to read the content of the file. To read this file, we will run the command `cat mission_brief.txt` to get the contents.

---

## Investigating the System (Linux)

### ① "Who Are You Logged In As?"

The simplest command in Linux also happens to be one of the most useful: `whoami` — This prints your current username.

### ② "What System Are You On?"

To see details about the operating system, kernel version, and architecture, use: `uname -a`
This gives a full line of system information — great for understanding exactly what environment you're working in.

*Example output:*
```
ubuntu@tryhackme:~$ uname -a
Linux tryhackme <REDACTED>-aws #17-Ubuntu SMP Mon Sep 2 13:48:07 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
```

**Breakdown of the information:**
- **Linux** – The system is running the Linux kernel.
- **tryhackme** – The hostname (the computer's name).
- **\<REDACTED\>-aws** – The kernel version installed on the machine.
- **x86_64** – The hardware platform (also 64-bit).
- **GNU/Linux** – The operating system type (Linux kernel + GNU tools).

If you only want the operating system name, you can try: `uname`

### ③ Check Disk and Storage Info

In real world environments, we will often need to check disk usage or available space, especially before running tools or analysing logs. A simple command for readable output is: `df -h` (`df -h`)

The `-h` means "human readable"; it shows sizes like 2G or 500M instead of long bytes — only numbers.

### ④ Read the System Files

Linux stores configuration and information files in the `/etc` directory. To practice navigating and reading files, head into `/etc` by running `cd /etc` and then list what's inside: `ls`

Let's now use `cat` to read the `os-release` file that almost every Linux system contains: `cat os-release`

This file provides details about the Linux distribution that are often clearer than those provided by the `uname` command.

---

## Windows CLI Basics

From a security perspective, Windows is important because many real-world attacks and investigations involve Windows systems.

### What is Windows Command Line?

The **Command Prompt** (often referred to as CMD) is a text-based interface for interacting with the Windows operating system. Instead of clicking folders and menus.

### Windows CLI Commands

#### ① Where Am I?
Check your current location by typing the command `cd`
This will show the full path of the directory you're currently in.

#### ② What's Around Me?
Lists the contents of the current directory using the command: `dir`
This command will list down the files and the folders present in the current directory.

#### ③ Are There Hidden Files?
Some files and folders on Windows are marked as hidden, which means they don't appear in a normal listing. To show everything, including hidden items, use: `dir /a`
It is important to note that hidden doesn't mean secret — it just means Windows hides them by default.

#### ④ Moving Around the File System
Let's use the `cd` command to navigate through the folders. We can use the format `cd <folder-name>` to move to the specified folder.
The command `cd Documents` will move us to the Documents folder.
To move back one level, we can use the `cd..` command.
Use the `dir` or `dir /a` command inside each folder to move to see what's there.

#### ⑤ Finding the File on the Disk
Instead of guessing where the file is, let Windows search for it. Use the following command: `dir /s task_brief.txt`
The `/s` flag tells Windows to search all subfolders starting from your current directory and show you the full path if the file exists.

#### ⑥ Navigate to the File
Let's use the `cd` command to navigate to the folder using the command format `cd <path_to_the_task_brief.txt>`. Use `dir` again to confirm that `task_brief.txt` is in the folder.

#### ⑦ Read the File
Now read the contents of the file using: `type task_brief.txt`
This will print the contents of the file directly in the command prompt.

---

## Gathering System Information on Windows

Learn how to ask the system questions about itself. Cybersecurity and IT professionals do this all the time. Before fixing a problem or investigating an incident, they first want to know:

- Who am I logged in as?
- What machine is this?
- What version of Windows is it running?
- How is it connected to the network?

### ① Who Am I Logged In As?
When working on a system, one of the first things to check is which user account you're using. This matters because different users can have different permissions.

Run the following command: `whoami`
This command prints the username of the account you're currently logged into.

### ② What Is the Name of This Computer?
Every Windows machine has a name. In workplaces, this helps identify network systems. To see this computer's name, run: `hostname`

### ③ What Version of Windows Is This?
Run: `systeminfo`

### ④ How Is This Machine Connected to the Network?
Run: `ipconfig`
This shows the machine's network configuration.

---

*Notes compiled from Module 5: Operating System Basics handwritten notes.*
