## Privilege escalation on Linux
### System/user info
`uname -a` Kernel version

`env` Environment variables

`whoami`

`history`

### Other users/history
`who`

`w`

`last`

### Sudoers check
`sudo -l` From sudo's man page:
```
     -l, --list  If no command is specified, list the allowed (and
                 forbidden) commands for the invoking user (or the user
                 specified by the -U option) on the current host. A
                 longer list format is used if this option is specified
                 multiple times and the security policy supports a
                 verbose output format.

                 If a command is specified and is permitted by the
                 security policy, the fully-qualified path to the
                 command is displayed along with any command line
                 arguments.  If command is specified but not allowed,
                 sudo will exit with a status value of 1.
```

Get superusers:
 `grep -v -E "ˆ#" /etc/passwd | awk -F: '$3 == 0 {print $1}'`
 
 ### Network check
 `ifconfig -a`

 `netstat -antup`
 
`lsof -a`

### Processes & software
`ps aux`

List versions of software in the machine (mysql, httpd, python, etc).

### SUID files
These are files that can be run as an admin from another user:

`find -perm -u=s -type f 2>/dev/null`

### Password hashes:

`cat /etc/shadow`

### Cron jobs:

`ls -la /etc/cron*`

Files that another user may be executing and that you can overwrite. If when analyzing the processes there are files that are being executed/copied/used at all by root, for instance, if you can modify those you can get root to run arbitrary code.

### Check for ssh keys:

`ls -la ~/.ssh`

Find passwords around:

`find . -type f -maxdepth 4 | xargs grep -i "password"`

## Search for vulnerabilities
Use `searchsploit` to see if the kernel is vulnerable.

`searchsploit kernel X.Y linux` | sort -n

## Resources
[Linux Privilege Escalation - Tradecraft Security Weekly #22](https://www.youtube.com/watch?v=oYHAi0cgur4)
