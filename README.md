# My Linux Upskill Challenge Journal
BITA Linux Challenge 9-14-26 to 10-15-26
BITA Kernel Crew · Cohort 1 · Sept 2026

## Day 0
- Set up my server (DigitalOcean) — it's alive 🐧
- Problems I hit and how I fixed them: No problems for day 0, just followed along with the setup.md and the live visual walkthrough.

## Day 1 — Get to Know Your Server: Assessment

### 1. Who am I?
You are logged into a remote Linux server. Determine the username of the account you are currently using.
#command used: whoami
Username: root
---

### 2. What Linux am I running?
Determine the Linux distribution and version running on your server.
#command used: lsb_release -a
The distribution name and version: Ubuntu 24.04.4 LTS
---

### 3. How long has this server been running?
Determine how long the server has been continuously running since its most recent boot.
#command used: uptime
The server's current uptime:11:57:36 up 15 min,  1 user,  load average: 0.00, 0.01, 0.02 
---

### 4. Identify the kernel
Determine the version of the Linux kernel currently running on the server.
#command used: uname -a (all) or -v (kernel version)
The kernel version: #139-Ubuntu SMP PREEMPT_DYNAMIC Sat Aug  1 03:52:05 UTC 2026
---

### 5. Who else is logged in?
Determine whether any other users currently have active sessions on the server.
#command used: w
The number of active login sessions and, if there are any, the usernames: 
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU  WHAT
root              68.131.29.19     11:42   23:12   0.00s  0.52s sshd: root@pts/0
---

### 6. Examine the CPU
Determine the architecture of the server's CPU and how many logical CPUs are available.
#command used: lscpu
The CPU architecture and logical CPU count: x86_64 and 1 logical CPU
---

### 7. Investigate the storage devices
Determine what block storage devices are attached to the server.
#command used: 
**Submit:** The names of the block devices and their approximate sizes.

---

### 8. Check memory availability

Determine how much physical memory the server has and how much is currently available for use.

**Submit:** Total memory and available memory.

---

### 9. Check filesystem capacity

Determine how much disk space is available on the filesystem containing the server's root directory.

**Submit:** Total capacity, used capacity, available capacity, and percentage used.

---

### 10. Identify the network connection

Determine the network interface currently being used by the server and identify its IPv4 address.

**Submit:** The interface name and IPv4 address.
