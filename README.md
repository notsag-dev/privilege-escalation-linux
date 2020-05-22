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
                 specified by the -U option) on the current host.  A
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
