# My Linux BITA Challenge Journal 9-14-26 to 10-15-26
### BITA Kernel Crew · Cohort 1 · Sept 2026

## Day 0
- Set up my server (DigitalOcean) — it's alive 🐧
- **Problems I hit and how I fixed them:**    
  No problems for day 0, I just followed along with the setup.md and the live visual walkthrough.
##

## Day 1 — Get to Know Your Server: Assessment
### 1. Who am I?  

You are logged into a remote Linux server. Determine the username of the account you are currently using. 

**_Command used:_** `whoami`  
**Username:** `root`
##


### 2. What Linux am I running?  

Determine the Linux distribution and version running on your server.  

**_Command used:_** `lsb_release -a`  
**The distribution name and version:** `Ubuntu 24.04.4 LTS`
##

### 3. How long has this server been running?  

Determine how long the server has been continuously running since its most recent boot.  

**_Command used:_** `uptime`  
**The server's current uptime:** `11:57:36 up 15 min, 1 user, load average: 0.00, 0.01, 0.02` 
##

### 4. Identify the kernel  

Determine the version of the Linux kernel currently running on the server.  

**_Command used:_** `uname -a (all) or -v (kernel version)`  
**The kernel version:** `#139-Ubuntu SMP PREEMPT_DYNAMIC Sat Aug 1 03:52:05 UTC 2026`
##

### 5. Who else is logged in?  

Determine whether any other users currently have active sessions on the server.  

**_Command used:_** `w`  
**The number of active login sessions and, if there are any, the usernames:**   
`USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU  WHAT`  
`root              68.131.29.19     11:42   23:12   0.00s  0.52s sshd: root@pts/0`
##

### 6. Examine the CPU

Determine the architecture of the server's CPU and how many logical CPUs are available.

**_Command used:_** `lscpu`  
**The CPU architecture and logical CPU count:** `x86_64 and 1 logical CPU`
##

### 7. Investigate the storage devices  

Determine what block storage devices are attached to the server.  

**_Command used:_** `lsblk`   
**The names of the block devices and their approximate sizes:**    
| NAME    | MAJ:MIN | RM  | SIZE | RO  | TYPE | MOUNTPOINTS |
| ------  |:-------:|:---:|:----:|:---:|:----:| ----------- |
| vda     | 253:0   | 0   | 10G  | 0   | disk |             |
| ├─vda1  | 253:1   | 0   | 9G   | 0   | part | /           |
| ├─vda14 | 253:14  | 0   | 4M   | 0   | part |             |
| ├─vda15 | 253:15  | 0   | 106M | 0   | part | /boot/efi   |
| └─vda16 | 259:0   | 0   | 913M | 0   | part | /boot       |
| vdb     | 253:16  | 0   | 490K | 1   | disk |             |  
##

### 8. Check memory availability  

Determine how much physical memory the server has and how much is currently available for use.  

**_Command used:_** `free -h`  
**Total memory and available memory:**    
|              | total     |  used     | free    | shared | buff/cache | available |  
| ------------ | ---------:| ---------:| -------:| ------:| ----------:| ---------:|  
| Mem:         | 458Mi     | 156Mi     | 45Mi    |  4.0Mi |      280Mi |     301Mi |  
| Swap:        |    0B     |    0B     |   0B    |
##

### 9. Check filesystem capacity  

Determine how much disk space is available on the filesystem containing the server's root directory.  

**_Command Used:_** `df -h`  
**Total capacity, used capacity, available capacity, and percentage used:**  
| Filesystem    | Size | Used | Avail | Use% | Mounted on  |
| ------------- | ----:| ----:| -----:| ----:| ----------- |
| tmpfs         |  46M | 1.0M |   45M |   3% | /run        |
| /dev/vda1     | 8.7G | 2.2G |  6.6G |  25% | /           |
| tmpfs         | 230M |    0 |  230M |   0% | /dev/shm    | 
| tmpfs         | 5.0M |    0 |  5.0M |   0% | /run/lock   |
| /dev/vda16    | 881M | 117M |  703M |  15% | /boot       |
| /dev/vda15    | 105M | 6.2M |   99M |   6% | /boot/efi   |
| tmpfs         |  46M |  12K |   46M |   1% | /run/user/0 |
##

### 10. Identify the network connection  

Determine the network interface currently being used by the server and identify its IPv4 address.  

**_Command used:_** `ifconfig`  
**The interface name and IPv4 address:** `eth0` and `159.89.84.175`
##

## Day 2 Assessment — Basic Navigation

### 1. Find your starting location

Determine the complete filesystem path of your current location.

**_Command used:_** `pwd`   
**The absolute path:** `/root`
##


### 2. Navigate using an absolute path

Move to the system directory that contains the server's log files.

**_Command used:_** `cd /var/log`  
**The absolute path of the directory you are now in:** `/var/log`

##

### 3. Navigate using a relative path

From the directory containing the system logs, move one level upward and then into its `log` directory again using **only a relative path**.

**_Command used:_** (move one level upward) `cd ..`, (into log directory again with relative path) `cd log`    
**The resulting absolute path:** `/var/log`

##

### 4. Return home

Without manually typing the full path to your home directory, return to your own home directory.

**_Command used:_** `cd`  
**The absolute path of your home directory:** `/root`

##

### 5. Find hidden files

Inspect your home directory and determine how many entries are hidden files or hidden directories.

**_Command used:_** `ls -a`  
**The number of hidden entries you find:** `14`

##

### 6. Identify directories

Display the contents of your home directory in a detailed listing and determine which entries are directories rather than ordinary files.

**_Command used:_** `ls -la`  
**The names of all directories in your home directory:** `., .., .cache, .cargo, .config, .local, .ssh, snap`

##

### 7. Create a directory structure

Inside your home directory, create this structure:

```text
linux-assessment/
└── day2/
    └── files/
```

**_Command sequence you used:_** (step 1): `mkdir linux-assessment`, (step 2): `cd linux-assessment`, (step 3): `mkdir day2`, (step 4): `cd day2`, (step 5): `mkdir files`  
**End result:** `/root/linux-assessment/day2/files`

##

### 8. Create and relocate a file

Create an empty file named `navigation-test` in your home directory. Then move it into the `files` directory you created in Question 7.

**_Command sequence you used:_** (step 1): `touch navigation-test`, (step 2): `mv navigation-test ./linux-assessment/day2/files`  
**Final path of the file:** `/root/linux-assessment/day2/files/navigation-test`

##

### 9. Move a directory

Create a directory named `archive` inside `linux-assessment`. Move the `files` directory into `archive`.

Your resulting structure should be:

```text
linux-assessment/
└── day2/
    └── archive/
        └── files/
            └── navigation-test
```

**_Command sequence you used:_** (step 1): `cd ./linux-assessment/day2`, (step 2): `mkdir archive`, (step 3): `mv files archive`  
**Final path of `navigation-test`:** `/root/linux-assessment/day2/archive/files/navigation-test`

##

### 10. Clean up

Remove everything you created for this assessment without deleting anything that existed in your home directory before you began.

**_Command sequence you used:_** (step 1): `rm ./linux-assessment/day2/archive/files/navigation-test`, (step 2): `rmdir ./linux-assessment/day2/archive/files`, (step 3): `rmdir ./linux-assessment/day2/archive`, (step 4): `rmdir ./linux-assessment/day2`, (step 5): `rmdir ./linux-assessment`  

**A listing demonstrating that your `linux-assessment` directory no longer exists:**   
**_Command used:_** `ls`  
**Results:** `snap` (directory remaining)

##

### Optional Challenge — Documentation

A Linux administrator does not need to memorize every command.

Without searching the web, use the documentation available on the server to determine **which command can show a concise description of another command based on a keyword or phrase**?

**The command you discovered and a one-sentence explanation of what it does:** `apropos`, `-search the manual page names and descriptions for instances of the keyword`.

##

## Day 3 — Power Trip! Assessment

### 1. Identify running processes

Determine which processes are currently running on your server.

**_Command used:_** `ps`

**The process ID and name of the process associated with your current shell:**   
| PID  | CMD  |
| ---- | ---- |
| 1069 | bash |
| 1208 | ps   |

##

### 2. Find the most resource-intensive process

Determine which currently running process is consuming the most CPU resources.

**_Command used:_** `top`

**Its process ID, name, and current CPU percentage:**
| PID  | Name | %CPU |
|:----:|:----:|:----:|
| 1321 | top  | 0.3  |

##

### 3. Investigate a process

Choose a running process other than your current shell and determine:

* Which user owns it
* Its process ID
* Its parent process ID

**All three values:* `root`, `1178`, `2` 

##

### 4. Find your shell's parent

Determine which process launched your current shell.

**The parent process's name and process ID:** `sshd`, `1068`

##

### 5. Run a command in the background

Start a command that will continue running for at least 30 seconds **without blocking your ability to enter additional commands**.

**_Command used:_** `sleep 10m &`

**The process ID assigned to the background process:** `2105`

##

### 6. Locate your background process

After starting the background process from Question 5, find it among the currently running processes.

**_Command used:_** `ps aux`  
**The process ID and current status:** `sleep`

##

### 7. Stop a process

Terminate the background process you created in Question 5.

**_Command used:_**  `kill 2105`  
**Evidence that the process is no longer running:** Ran `ps aux` and at the bottom is says `sleep 10m Terminated`

##

### 8. Find a process by name

Determine whether there are currently any processes running that belong to the SSH service.

**_Command used:_** pgrep -a ssh
**The process ID(s) and process name(s), if present:**
|  PID  | Process Name |
|:-----:|:------------:|
| 957   | sshd         |
| 958   | sshd         |
| 1068  | sshd         |

##

### 9. Monitor the system

Open a live view of the processes running on the server. Identify the process currently consuming the most memory.

**_Command used:_** `top`

**Its process ID, name, and memory percentage:** 
| PID  | Process Name | %Mem |
|:----:|:------------:|:----:|
|   1  | systemd      | 2.8  |

##

### 10. Become another user

Switch from your normal account to the administrative account available on your training server.

Once switched, verify that your identity has changed.

**_Commands used:_** `sudo -i`, `whoami`, and `exit`

**The username of the account you switched to, then return to your original account:** 
```
(Step 1) Switched from user tonelo4 to root user using the sudo -i command.  
(Step 2) Verified using the whoami command.  
(Step 3) Used the exit command to exit root user and returned to user tonelo4.  
(Step 4) Verified again using the whoami command.
```

##

### Practical Challenge

You accidentally start a command that continues running and appears to have taken control of your terminal.

**Without closing your SSH connection**, regain control of the terminal while leaving the command available to be resumed later.

**Describe what you did and whether the command is still running afterward:**
```
(Step 1): Used a bash command to run test.sh which created a counter by ones.
(Step 2): Since this was running on the foreground, I just hit 'CTRL-z' to stop the process.
(Step 3): Used 'bg %1' to resume the bash test.sh (the '1' is the job number) from where it left off, but this time 'CTRL-z' was ineffective for background processes.
(Step 4): Used 'ps aux' to retrieve the PID or just use 'kill %1' to terminate the process without closing the SSH connection.
```

This is particularly useful because it tests whether students understand **foreground vs. background processes and job control**, rather than merely memorizing process-management commands.

##

## Day 4 — Installing Software & Exploring the File Structure

### 1. Identify the package manager

Determine which package-management system your Linux distribution uses.

**The package manager's name:** Using Ubuntu 24.04.4, which is a debian-based distribution, so `apt` is the package manager.

##

### 2. Find a package

Using the software repositories configured on the server, determine whether a text editor named **nano** is available for installation.

**_Command used:_** `apt search "nano"`  
**Whether it is available and the version that would be installed:**    
`nano/noble-updates, noble-security 7.2-2ubuntu0.2 amd64 [installed, automatic]`

##

### 3. Install software

Install **nano** using the system's normal software-management mechanism.

**_Command used:_** `sudo apt install nano`

**Evidence that the installation completed successfully:**
```
nano is already the newest version (7.2-2ubuntu0.2).
nano set to manually installed
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
```
##

### 4. Verify the installation

Determine where the executable for the newly installed text editor is located.

**The complete filesystem path to the executable:** `/usr/bin/nano`

##

## 5. Find installed files

Determine which files were installed as part of the **nano** package.

**At least three paths belonging to the installed package:**  
`/usr/share`, 
`/usr/share/man/man1/nano.1.gz`, 
`/usr/share/nano/autoconf.nanorc`

##

### 6. Explore `/etc`

Investigate the `/etc` directory and identify the file that contains information about the Linux distribution currently running on the server.

**The complete path to the file and the distribution name/version contained within it:**
`/etc/os-release`
Name = `Ubuntu`
Version = `24.04.4 LTS (Noble Numbat)`

##

### 7. Explore `/var`

Investigate `/var` and locate the directory where system log files are normally stored.

**Its complete filesystem path and the names of three log files found there:**
`/var/log`
`apport.log`, `auth.log`, and `syslog`

##

### 8. Explore `/usr`

Locate the directory under `/usr` that contains the majority of user-facing executable programs.

**The complete path and the names of three programs found there:**
`/usr/bin`
`tcpdump`, `bash`, and `netstat`

##

### 9. Identify configuration vs. data

Find one configuration file somewhere under `/etc` and one log file somewhere under `/var`.

**The complete path of each file and a one-sentence explanation of what type of information each contains:**
`/etc/debconf.conf` - main config file for debconf that tell debconf where to store data.
`/var/log/dpkg.log` - logs history of installs, upgrades, removals, and purges of packages.

##

### 10. Remove installed software

Uninstall **nano** using the system's package-management mechanism.

Afterward, verify that the program is no longer available as an installed package.

**Evidence that the package has been successfully removed:**
`2026-09-20 21:22:05 remove nano:amd64 7.2-2ubuntu0.2 <none>` in dpkg.log file,  
`-bash: /usr/bin/nano: No such file or directory` when using the command: `nano testfile.txt`

##

### Practical Challenge — Find the Right Place

You need to investigate a Linux server and are told:

> “The configuration is probably under `/etc`, temporary/runtime information is somewhere under `/run`, logs are under `/var`, and installed programs are primarily under `/usr`.”

Without using a graphical file manager or searching the web, investigate these areas and identify **one interesting or useful file/directory in each location**.

* `/etc`: `/etc/adduser.conf` + the configuration file with the default settings for `adduser` 
* `/run`: `/run/multipath` + used to detect and coalesce multiple paths to devices
* `/var`: `/var/log` + where system log files are stored
* `/usr`: `/usr/bin` + directory where executable programs are stored

##

## Day 5 — More or Less

### 1. Determine file size

Find a file in `/var/log` that is larger than 1 KB.

**_Command used:_** `ls -lh`  
**The file's complete path and its size:** `/var/log/syslog.1` and file size is `1.5M`

##


### 2. Compare file sizes

Identify the three largest regular files in a directory of your choice under `/var/log`.

**_Command used:_** `ls -lhS`
**Their paths and sizes, ordered from largest to smallest:**   
`/var/log/syslog.1` and file size is `1.5M`  
`/var/log/cloud-init.log.1` and file size is `1.2M`  
`/var/log/syslog` and file size is `833K`  

##

### 3. Count lines

Choose a text-based log file under `/var/log` and determine how many lines it contains.

**_Command used:_** `sudo wc -l syslog`  
**The filename and number of lines:** `syslog` and `6115`

##

### 4. Count words

Using the same log file, determine how many words it contains.

**_Command used:_** `sudo wc -w syslog`
**The filename and word count:** `syslog` and `63545`

##

### 5. Count characters

Determine the number of characters contained in the same log file.

**_Command used:_** `sudo wc -m syslog`
**The filename and character count:** `syslog` and `854620`

##

### 6. Examine a large file safely

Choose a log file containing enough text that displaying its entire contents would produce a substantial amount of terminal output.

Determine:

* What the first 10 lines contain
* What the last 10 lines contain

**A brief description of each section:** Used the command: `sudo head syslog.1` to show the first 10 lines of the syslog.1 file.  
Used the command: `sudo tail syslog.1` to show the last 10 lines of the syslog.1 file.

##

### 7. Search within a file

Choose a system log containing multiple entries and locate all entries containing a word of your choice that appears at least five times.

**_Command used:_** `grep "nano" dpkg.log`  
**The search term and number of matching lines:** search of the word `nano` came back with 12 matching lines results.

##

### 8. Search case-insensitively

Find occurrences of the word **error** in a suitable log file, treating `error`, `Error`, `ERROR`, etc. as equivalent.  
**_Command used:_** `sudo grep -i --color=auto error syslog.1` (to see the actual results)   
`sudo grep -ic --color=auto error syslog.1` (for the number of matching lines)

**The number of matching lines:** `15`

##

### 9. Combine filtering and counting

Find how many lines in a suitable log file contain the word **warning** (case-insensitive).  

**_Command used:_** `sudo grep -ic error syslog.1`  

**The number of matching lines and the filename examined:** `8` and `syslog.1`

##

### 10. Inspect output one screen at a time

Choose a sufficiently large text file and examine its contents without allowing the entire file to scroll past the terminal at once.

While examining it, locate a particular piece of information near the middle of the file.

**The information you found and describe how you navigated through the file:**  
I used the command `sudo more /var/log/auth.log` to access the auth.log file. I used `more` instead of `less` because `more` gives you the percentage of the document you've gone through so far. I used the down arrow key to go down the document, which got me to 47% and from there I used the Enter key to get down the 50%. In the auth.log file, I see the session open and session closed from where I used the sudo command to gain root access at the time stamp provided.

##

### Practical Challenge — Investigate a Log

Choose one substantial log file under `/var/log`.

**_File used:_** `syslog.1`

Without opening it in a graphical editor, determine:
1. Its size. **_Command used:_** `ls -lh syslog.1`  
**_Results:_** `846K` 
2. Its number of lines. **_Command used:_** `sudo wc -l syslog.1`  
**_Results:_** `6202`
3. The first line. **_Command used:_** `sudo head -1 syslog.1`  
**_Results:_** `2026-09-20T15:59:29.471951+00:00 Tone-the-Server-September2026 systemd-modules-load[297]: Module 'i2c_dev' is built in`
4. The last line. **_Command used:_** `sudo head -1 syslog.1`  
**_Results:_** `2026-09-21T22:27:07.966551-04:00 Tone-the-Server-September2026 systemd[1]: Stopped snapd.seeded.service - Wait until snapd is fully seeded.`
5. The three most common-looking message types or keywords you can identify. **_Command used:_** `sudo less syslog.1`  
**_Results:_** Three most common keywords identified: `Finished`, `Starting`, and `Listening`
6. How many lines contain `error` or `warning`, ignoring capitalization. **_Command used:_** `sudo grep -ic error syslog.1` and `sudo grep -ic error syslog.1`  
**_Results:_** `15` and `8` 

##

## Day 6 — Editing Text Files

### 1. Create a text file

Create a new text file in your home directory named `day6-notes.txt`.

**_Command used:_** `vim day6-notes.txt`  
**The complete path to the file:** `/home/tonelo4/day6-notes.txt`

##

### 2. Add information

Put the following three lines into the file:

```text
Linux
System Administration
Day 6
```

**Evidence that the file contains exactly those three lines:**  

<img width="655" height="78" alt="Day 6 #2 " src="https://github.com/user-attachments/assets/39ce630b-568c-4e4c-87a2-ddfe621a64fd" />


---

### 3. Modify existing content

Change the third line so that it contains the current day of the week instead of `Day 6`.

**The resulting contents of the file:**

<img width="625" height="96" alt="Day 6 #3 " src="https://github.com/user-attachments/assets/0f0dfc4f-f689-4484-9d28-760b9ac35061" />


##

### 4. Add a line

Add a fourth line containing your Linux distribution's name.

**The resulting contents:**

<img width="667" height="245" alt="Day 6 #4 " src="https://github.com/user-attachments/assets/10718d90-7638-4b85-a8e2-3eee2c4f1da8" />


##

### 5. Delete a line

Remove the line containing `System Administration`.

**_Command used:_** `dd`  

**The resulting contents:**

<img width="602" height="97" alt="Day 6 #5 " src="https://github.com/user-attachments/assets/e73aa5ab-1ae6-4144-a3b4-584c9a695581" />


##

### 6. Search within a text file

Open a suitable text file containing enough lines to make manually locating text inconvenient. Find a specific word or phrase within the file.

**_Command use:_** `vim services`, and `/server\c`

**The word or phrase you located and the line on which it appears:**  
`server` and `line 32`

<img width="1097" height="308" alt="Day 6 #6 " src="https://github.com/user-attachments/assets/aef64024-37d6-4d0a-810d-7de144b3dc6e" />


##

### 7. Make a backup

Create a backup copy of `day6-notes.txt` named `day6-notes.bak`.

**The names and locations of both files:*
`day6-notes.txt` and `day6-notes.bak`  
`/home/tonelo4/day6-notes.txt` and `home/tonelo4/day6-notes.bak`

<img width="900" height="92" alt="image" src="https://github.com/user-attachments/assets/580bdd07-9da3-4ff0-a9a7-962e353f7d8a" />


##

### 8. Compare two files

Modify `day6-notes.txt` so that it differs from `day6-notes.bak`.

Determine exactly what changed between the two files.

**A description of the difference:**  
Today's date was added to the `day6-notes.txt` file on line 4 and saved. cat was run on both the .txt file and the .bak backup to show the .txt with the added date and .bak without. ls -l was also ran to show that the file size was now larger with the .txt compared to the .bak.

<img width="597" height="247" alt="Day 6 #8 " src="https://github.com/user-attachments/assets/016005f0-c3e6-4104-a5e5-317c1bc124df" />

##

### 9. Edit a system configuration file safely

Locate a configuration file under `/etc` that is appropriate for inspection.

Make a backup of it **before making any changes**. Add a harmless comment to the configuration file, then verify that the comment was added.

**The file you selected and the location of your backup:** `crontab` and `/etc/crontab`

<img width="962" height="46" alt="Day 6 #9-1 " src="https://github.com/user-attachments/assets/4bbb58b1-78b3-4d97-846d-75d9f98a3093" />


<img width="847" height="47" alt="Day 6 #9-2" src="https://github.com/user-attachments/assets/0530f262-d5cf-43bf-b46f-92ee238572c4" />


<img width="1140" height="497" alt="Day 6 #9-3" src="https://github.com/user-attachments/assets/6f817b87-be68-4940-9db8-60f34a5641d1" />


<img width="1352" height="575" alt="Day 6 #9-4" src="https://github.com/user-attachments/assets/adae5e6e-1e9e-4e93-8691-503b22e149b4" />


<img width="1241" height="582" alt="Day 6 #9-5" src="https://github.com/user-attachments/assets/7e0fef93-df70-4c90-b810-b6503311aff4" />


<img width="857" height="42" alt="Day 6 #9-6" src="https://github.com/user-attachments/assets/a2d7a7ec-8b32-49d0-bedc-aec4bea20d6f" />  


**Important:** Do not modify an active setting or otherwise change system behavior.

##

### 10. Recover from a mistake

Using `day6-notes.txt`, deliberately make a small change and then restore the file to its previous contents using the backup you created earlier.

**Evidence that the restored file matches the backup:**

<img width="876" height="280" alt="Day 6 #10-1" src="https://github.com/user-attachments/assets/9181bc0b-9c4c-4066-b757-dff38d05e39f" />


<img width="945" height="220" alt="Day 6 #10-2" src="https://github.com/user-attachments/assets/5a50ae2e-d3b5-45a6-844c-4129753056ea" />


<img width="935" height="230" alt="Day 6 #10-3" src="https://github.com/user-attachments/assets/8e783ff6-8b09-4a8f-bcdf-f1eaa7412066" />


<img width="905" height="52" alt="Day 6 #10-4" src="https://github.com/user-attachments/assets/4640e3da-a57a-43cc-9e7e-6b82bef1e7f7" />


##

### Practical Challenge — Configuration Investigation

Choose a configuration file under `/etc` that you have permission to read.

Using a text editor and other tools available on the server:

1. Determine what the file controls.
<img width="1442" height="207" alt="Day 6 practical challenge-1" src="https://github.com/user-attachments/assets/1162833b-889b-4ed3-9ba9-7dcb9c783604" />

2. and 3. Identify three configuration settings and Identify any comments explaining those settings.
<img width="1002" height="451" alt="Day 6 practical challenge-2 and 3" src="https://github.com/user-attachments/assets/f1cf58f3-886a-4b64-8806-64e3c8f4d74b" />

4. Make a backup.
<img width="1097" height="45" alt="Day 6 practical challenge-4" src="https://github.com/user-attachments/assets/d0178444-23ae-49f1-b581-e39d786fcbf7" />

<img width="757" height="145" alt="Day 6 practical challenge-4-1" src="https://github.com/user-attachments/assets/c82e83f4-416b-459d-8d7f-3246d887a7b0" />


5., 6., and 7. Add a harmless comment identifying that you inspected the file, Save the change, and Verify that the change persisted.
<img width="1090" height="561" alt="Day 6 practical challenge-5-7" src="https://github.com/user-attachments/assets/46bc0682-3e7e-48bf-aadf-7202c857c01c" />

##


## Day 7 — The Server and Its Services

### 1. Install a web server

Turn your Linux server into a functioning HTTP web server using software available from its configured package repositories.

**The name and version of the web-server software you installed:**

<img width="1460" height="212" alt="Day 7 #1-1" src="https://github.com/user-attachments/assets/a0fc9414-44ae-428c-8953-52950aee8320" />

<img width="671" height="70" alt="Day 7 #1-2" src="https://github.com/user-attachments/assets/15ee3339-4ad2-43d9-a9c6-2aa234fb30c1" />

##

### 2. Verify that the service is running

Determine whether your newly installed web server is currently running.

**Its current service state:**

<img width="1120" height="345" alt="Day 7 #2" src="https://github.com/user-attachments/assets/08a98a83-315b-428a-8903-ef42e4179730" />

##

### 3. Access the server remotely

From a separate computer or browser, connect to your server using its public network address.

**The HTTP response or webpage you receive:**

<img width="1621" height="916" alt="Day 7 #3" src="https://github.com/user-attachments/assets/690d0e53-4b57-4ede-be9b-d82ed4f180f6" />

##

### 4. Stop the web service

Temporarily stop the web server.

Then attempt to access the server from your browser again.

**Describe what changed:**

<img width="1191" height="237" alt="Day 7 #4-1" src="https://github.com/user-attachments/assets/ac040823-222a-4ba7-bdd8-67bb0954bcef" />

<img width="1597" height="887" alt="Day 7 #4-2" src="https://github.com/user-attachments/assets/e09042da-76b9-4667-879a-b6c3d9a82b58" />

##

### 5. Start the service again

Restore the web server to its running state.

**Evidence that the service is running again and that the webpage is accessible:**

<img width="1215" height="355" alt="Day 7 #5-1" src="https://github.com/user-attachments/assets/9649b6ef-c8aa-4f99-887e-62c26079f85e" />

<img width="1612" height="932" alt="Day 7 #5-2" src="https://github.com/user-attachments/assets/a4999ae4-0c45-452f-bf08-51c3e79ed4cd" />

##

### 6. Locate the web server configuration

Explore the filesystem and identify the directory containing the web server's primary configuration files.

**The directory path and the names of three configuration files found there:**

<img width="1415" height="117" alt="Day 7 #6" src="https://github.com/user-attachments/assets/819009b8-21a6-4eea-ad39-3629a441b055" />

##

### 7. Find the website's document root

Determine which directory contains the files served by the default website.

**The directory's complete path:**

<img width="1170" height="345" alt="Day 7 #7" src="https://github.com/user-attachments/assets/a9f1d1e7-177b-422e-ac85-d4a8ed2da96e" />

##

### 8. Customize the website

Replace the default webpage with a simple page containing:

> **Linux Upskill Challenge — Day 7**

You may use plain text or HTML.

**The URL of your server and the text displayed by the page:**

<img width="757" height="150" alt="Day 7 #8-1" src="https://github.com/user-attachments/assets/2c555324-7240-4693-a75a-a37d5f6a8920" />

<img width="1678" height="832" alt="Day 7 #8-2" src="https://github.com/user-attachments/assets/adfe25ae-ce96-49f3-863f-03d676c6e04c" />

##

### 9. Investigate the access log

Visit your customized webpage several times from your browser.

Then locate the web server's access log and determine which entries correspond to your visits.

**The number of requests generated by your visits and the HTTP status code returned:**

<img width="1162" height="167" alt="Day 7 #9-1" src="https://github.com/user-attachments/assets/4ae4941f-ffa0-49b9-98e3-5b2f3c2947ae" />

<img width="1163" height="325" alt="Day 7 #9-2" src="https://github.com/user-attachments/assets/74f25201-e122-4f00-ae52-d55d14ad5b33" />

##

### 10. Investigate the error log

Locate the web server's error log and determine whether it currently contains any errors.

**Whether errors are present. If so, provide the timestamp and a brief description of one:**

<img width="1163" height="288" alt="Day 7 #10" src="https://github.com/user-attachments/assets/d745b836-47f1-455d-97ce-fc2ac0dcdbcb" />

##

## Practical Challenge — Break and Restore the Web Server

Your web server is running, but the webpage suddenly becomes unavailable.

Without reinstalling the web server:

1. Determine whether the service is running.
2. If it is stopped, restore it.
3. If it is running, investigate its configuration and logs.
4. Restore the webpage so it is accessible again.
5. Verify the final service state.

**A brief incident report containing:**
* What you discovered
* What you changed
* How you determined the problem was resolved

<img width="1002" height="352" alt="Day 7 PC-IR" src="https://github.com/user-attachments/assets/d253abb5-4fc6-4d76-a581-7970d4e982d8" />

This challenge is particularly useful because it tests the central Day 7 concept: **a server application is more than a program—it has configuration, a managed service, content, and logs that can be investigated independently.** 

<img width="1621" height="720" alt="Day 7 PC-1" src="https://github.com/user-attachments/assets/6d435f72-c887-476d-b711-c753878307b3" />

<img width="1461" height="450" alt="Day 7 PC-2" src="https://github.com/user-attachments/assets/b7b27c9c-90fe-4f35-b280-be1c9207ead3" />

<img width="1437" height="677" alt="Day 7 PC-3_1" src="https://github.com/user-attachments/assets/af6a310a-277f-438e-a6c6-045dc55235f2" />

<img width="1462" height="225" alt="Day 7 PC-3_2" src="https://github.com/user-attachments/assets/dd89ca5c-d9ab-4e07-ba4a-0abd2fa8b09c" />

<img width="1461" height="211" alt="Day 7 PC-3_3" src="https://github.com/user-attachments/assets/68e1c583-74c0-47d6-9054-fa3661705b62" />

<img width="1467" height="205" alt="Day 7 PC-3_4" src="https://github.com/user-attachments/assets/a2dc7dd2-27c4-47da-be30-e4a98f668c65" />

<img width="1462" height="250" alt="Day 7 PC-3_5" src="https://github.com/user-attachments/assets/16c7c318-bab4-4c65-bf2b-c66a5f7584e0" />

<img width="1207" height="405" alt="Day 7 PC-4" src="https://github.com/user-attachments/assets/362fbd6a-9a2c-4edb-8f7b-01ef6b8bf834" />

<img width="1450" height="450" alt="Day 7 PC-5" src="https://github.com/user-attachments/assets/a85ff377-c03b-440d-b236-f2530ffb0ebb" />

##


## Day 8 — Text Processing & Log Analysis

### 1. Examine the web server log

Locate the web server's access log and inspect its contents.

**Submit:** The path to the log and the date/time of the most recent request recorded in it.

---

### 2. Navigate a large text file

Open the web server's access log in a way that allows you to move both forward and backward through the file without dumping the entire file onto the terminal.

Find the **first occurrence of an HTTP 404 response**.

**Submit:** The corresponding log entry.

---

### 3. Search for failed requests

Determine how many requests in the web server's access log resulted in an HTTP 404 response.

**Submit:** The number of matching requests.

---

### 4. Examine recent activity

Determine the **10 most recent entries** in the web server's access log.

**Submit:** The 10 entries, or the timestamp and requested resource for each.

---

### 5. Follow the log in real time

Begin monitoring the web server's access log for new entries.

While monitoring it, load your website in a browser.

**Submit:** The new log entry generated by your browser request.

---

### 6. Investigate authentication activity

Locate the system's authentication log and identify unsuccessful login attempts involving the administrative account.

**Submit:** The number of unsuccessful attempts currently recorded.

---

### 7. Exclude a particular user

From the authentication log, identify unsuccessful authentication attempts that **did not involve the administrative account**.

**Submit:** Three example log entries, if at least three exist.

---

### 8. Extract information from log entries

From the unsuccessful authentication records, extract **only the IP addresses** associated with those attempts.

**Submit:** The resulting list of IP addresses.

---

### 9. Identify unique sources

Take the IP-address list from Question 8 and determine which addresses occur more than once.

**Submit:** Each repeated IP address and the number of times it occurs.

---

### 10. Redirect your results

Create a file named `~/day8-results.txt` containing the IP addresses of unsuccessful authentication attempts against the administrative account.

The file should contain **only the extracted IP addresses**, rather than the complete log entries.

**Submit:** The file's contents and its location.

##

## Day 9 — Networking & Firewalls

### 1. Identify listening ports

Determine which TCP ports currently have services listening on your server.

**Submit:** The port numbers and the service associated with each one.

---

### 2. Identify the owning processes

For each publicly accessible listening TCP port you found, determine which process is responsible for it.

**Submit:** Port number, process name, and process ID.

---

### 3. Examine network exposure

Determine which listening services are bound only to the local machine and which are potentially reachable through the server's network interfaces.

**Submit:** One example of each, if both exist.

---

### 4. Scan the server

Perform a port scan against the server itself.

**Submit:** Every open TCP port discovered and the service associated with each.

---

### 5. Compare two views

Compare the results of your local inspection of listening sockets with the results of your port scan.

**Submit:** Any differences you find and a brief explanation of why the two methods might produce different results.

---

### 6. Inspect the firewall

Determine whether a host-based firewall is currently active and identify its existing rules.

**Submit:** Whether it is active and a summary of its current inbound rules.

---

### 7. Protect SSH

Before modifying the firewall, establish a second SSH session to the server and keep both sessions open.

Create a copy to the server's current firewall configuration. 

Now, configure the server's firewall so that SSH remains accessible while unsolicited incoming connections to the HTTP service are blocked.

After your changes, test creating a 3rd SSH connection. Do not close either existing SSH session until you have verified that a new SSH connection can also be established successfully.

Try to be very careful with this challenge, as you can risk completely blocking access to your own server.  If you lock yourself out, you may have to destroy the server and create a new one.

Submit: The firewall rule(s) you added and evidence that a new SSH connection succeeds.

---

### 8. Verify the firewall externally

From a separate machine, attempt to access the server's web service after applying the firewall change.

**Submit:** Whether the connection succeeds or fails.

---

### 9. Restore web access

Modify the firewall configuration so that the web server is accessible again while SSH remains permitted.

**Submit:** Evidence that the website is reachable and that SSH remains allowed.

---

### 10. Security inventory

Create a short inventory of the network services currently exposed by your server.

For each exposed service, record:

* Port
* Protocol
* Service
* Process
* Whether the service is intentionally exposed

**Submit:** Your completed inventory.
