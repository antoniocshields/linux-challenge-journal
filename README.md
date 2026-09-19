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

