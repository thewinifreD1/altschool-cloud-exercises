1
## Ensure nodev option set on /tmp partition (Automated)

### Profile Applicability:

- Level 1 - Server
- Level 1 - Workstation

### Description:
The **nodev** mount option specifies that the filesystem cannot contain special devices.

### Rationale:
Since the /tmp filesystem is not intended to support devices, set this option to ensure that
users cannot attempt to create block or character special devices in /tmp .

### Audit:
Verify that the nodev option is set if a /tmp partition exists

Run the following command and verify that nothing is returned:

 `findmnt -n /tmp | grep -v nodev`
 
### Command Output 
 
```ruby
root@ubuntu-focal:~# findmnt -n /tmp | grep -v nodev
root@ubuntu-focal:~# 
```

2
### Ensure noexec option set on /tmp partition (Automated)

### Profile Applicability:

- Level 1 - Server
- Level 1 - Workstation

### Description:
The **noexec** mount option specifies that the filesystem cannot contain executable binaries.

### Rationale:
Since the /tmp filesystem is only intended for temporary file storage, set this option to
ensure that users cannot run executable binaries from /tmp.

### Audit:
If a /tmp partition exists, verify that the noexec option is set.
Run the following command and verify that nothing is returned:

`# findmnt -n /tmp | grep -v noexec`

### Command Output

```ruby
root@ubuntu-focal:~# findmnt -n /tmp | grep -v noexec
root@ubuntu-focal:~# 
```

3
### Ensure DHCP Server is not installed (Automated)

### Profile Applicability:

- Level 1 - Server
- Level 1 - Workstation

### Description:
The Dynamic Host Configuration Protocol (DHCP) is a service that allows machines to be
dynamically assigned IP addresses.

### Rationale:
Unless a system is specifically set up to act as a DHCP server, it is recommended that this
package be removed to reduce the potential attack surface.

### Audit:
Run the following commands to verify isc-dhcp-server is not installed:

`# dpkg -s isc-dhcp-server | grep -E '(Status:|not installed)'`
`dpkg-query: package 'isc-dhcp-server' is not installed and no information is
available`

### Command Output

```ruby
root@ubuntu-focal:~# dpkg -s isc-dhcp-server | grep -E '(Status:|not installed)'
dpkg-query: package 'isc-dhcp-server' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files.
root@ubuntu-focal:~#
```

4
### Ensure LDAP server is not installed (Automated)

### Profile Applicability:
- Level 1 - Server
- Level 1 - Workstation

### Description:
The Lightweight Directory Access Protocol (LDAP) was introduced as a replacement for
NIS/YP. It is a service that provides a method for looking up information from a central
database.

### Rationale:
If the system will not need to act as an LDAP server, it is recommended that the software be
removed to reduce the potential attack surface.

### Audit:
Run the following command to verify slapd is not installed:

`# dpkg -s slapd | grep -E '(Status:|not installed)'
dpkg-query: package 'slapd' is not installed and no information is available`

### output

```ruby
root@ubuntu-focal:~# dpkg -s slapd | grep -E '(Status:|not installed)'
dpkg-query: package 'slapd' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files.
root@ubuntu-focal:~#
```

5
### Ensure wireless interfaces are disabled (Automated)

### Profile Applicability:
- Level 1 - Server
- Level 2 - Workstation

### Description:
Wireless networking is used when wired networks are unavailable. Debian contains a
wireless tool kit to allow system administrators to configure and use wireless networks.

### Rationale:
If wireless is not to be used, wireless devices can be disabled to reduce the potential attack
surface.

### Impact:
Many if not all laptop workstations and some desktop workstations will connect via
wireless requiring these interfaces be enabled.

### Audit:
Run the following script to verify no wireless interfaces are active on the system:

`#!/bin/bash
if command -v nmcli >/dev/null 2>&1 ; then
 if nmcli radio all | grep -Eq '\s*\S+\s+disabled\s+\S+\s+disabled\b'; then
 echo "Wireless is not enabled"
 else
 nmcli radio all
 fi
elif [ -n "$(find /sys/class/net/*/ -type d -name wireless)" ]; then
 t=0
 mname=$(for driverdir in $(find /sys/class/net/*/ -type d -name wireless |
xargs -0 dirname); do basename "$(readlink -f
"$driverdir"/device/driver/module)";done | sort -u)
 for dm in $mname; do
 if grep -Eq "^\s*install\s+$dm\s+/bin/(true|false)"
/etc/modprobe.d/*.conf; then
 /bin/true
 else
 echo "$dm is not disabled"
 t=1
 fi
 done
 [ "$t" -eq 0 ] && echo "Wireless is not enabled"
else
 echo "Wireless is not enabled"
fi`
Output should be:
`Wireless is not enabled`

### command output

```ruby
root@ubuntu-focal:~# #!/bin/bash
root@ubuntu-focal:~# if command -v nmcli >/dev/null 2>&1 ; then
>  if nmcli radio all | grep -Eq '\s*\S+\s+disabled\s+\S+\s+disabled\b'; then
>  echo "Wireless is not enabled"
>  else
>  nmcli radio all
>  fi
> elif [ -n "$(find /sys/class/net/*/ -type d -name wireless)" ]; then
>  t=0
>  mname=$(for driverdir in $(find /sys/class/net/*/ -type d -name wireless |
bash: command substitution: line 32: syntax error: unexpected end of file    
bash: command substitution: line 32: syntax error: unexpected end of file
> xargs -0 dirname); do basename "$(readlink -f
> "$driverdir"/device/driver/module)";done | sort -u) 
>  for dm in $mname; do
>  if grep -Eq "^\s*install\s+$dm\s+/bin/(true|false)"
> /etc/modprobe.d/*.conf; then
>  /bin/true
>  else
>  echo "$dm is not disabled"
>  t=1
>  fi
>  done
>  [ "$t" -eq 0 ] && echo "Wireless is not enabled"
> else
>  echo "Wireless is not enabled"
> fi
Wireless is not enabled
root@ubuntu-focal:~#
```

6
### Ensure ufw is installed (Automated)

Profile Applicability:
- Level 1 - Server
- Level 1 - Workstation

### Description:
The Uncomplicated Firewall (ufw) is a frontend for iptables and is particularly well-suited
for host-based firewalls. ufw provides a framework for managing netfilter, as well as a
command-line interface for manipulating the firewall

### Rationale:
A firewall utility is required to configure the Linux kernel's netfilter framework via the
iptables or nftables back-end.
The Linux kernel's netfilter framework host-based firewall can protect against threats
originating from within a corporate network to include malicious mobile code and poorly
configured software on a host.
Note: Only one firewall utility should be installed and configured. UFW is dependent on the
iptables package

### Audit:
Run the following command to verify that Uncomplicated Firewall (UFW) is installed:

`# dpkg -s ufw | grep 'Status: install'
Status: install ok installed`

### output

```ruby
root@ubuntu-focal:~# dpkg -s ufw | grep 'Status: install'
Status: install ok installed
root@ubuntu-focal:~#
```

7
### Ensure cron daemon is enabled and running (Automated)

### Profile Applicability:
- Level 1 - Server
- Level 1 - Workstation

### Description:
The cron daemon is used to execute batch jobs on the system.
Note: Other methods, such as systemd timers, exist for scheduling jobs. If another method is
used, cron should be removed, and the alternate method should be secured in accordance
with local site policy

### Rationale:
While there may not be user jobs that need to be run on the system, the system does have
maintenance jobs that may include security monitoring that have to run, and cron is used
to execute them.

### Audit:
Run the following command to verify cron is enabled:

`# systemctl is-enabled cron
enabled`

### output

```ruby
root@ubuntu-focal:~# systemctl is-enabled cron
enabled
root@ubuntu-focal:~# 
```

8
### Ensure cron is restricted to authorized users (Automated)

### Profile Applicability:
- Level 1 - Server
- Level 1 - Workstation

### Description:
Configure /etc/cron.allow to allow specific users to use this service. If /etc/cron.allow
does not exist, then /etc/cron.deny is checked. Any user not specifically defined in this file
is allowed to use cron. By removing the file, only users in /etc/cron.allow are allowed to
use cron.
Notes:
- Other methods, such as systemd timers, exist for scheduling jobs. If another method is
used, cron should be removed, and the alternate method should be secured in
accordance with local site policy
- Even though a given user is not listed in cron.allow, cron jobs can still be run as that
user
- The cron.allow file only controls administrative access to the crontab command for
scheduling and modifying cron jobs

### Rationale:
On many systems, only the system administrator is authorized to schedule cron jobs. Using
the cron.allow file to control who can run cron jobs enforces this policy. It is easier to
manage an allow list than a deny list. In a deny list, you could potentially add a user ID to
the system and forget to add it to the deny files.

### Audit:
Run the following command and verify that /etc/cron.deny does not exist:

`# stat /etc/cron.deny
stat: cannot stat `/etc/cron.deny': No such file or directory`

### output

```ruby
root@ubuntu-focal:~# stat /etc/cron.deny
stat: cannot stat '/etc/cron.deny': No such file or directory
root@ubuntu-focal:~# 
```


9
### Ensure sudo is installed (Automated)

### Profile Applicability:
- Level 1 - Server
- Level 1 - Workstation

### Description:
sudo allows a permitted user to execute a command as the superuser or another user, as
specified by the security policy. The invoking user's real (not effective) user ID is used to
determine the user name with which to query the security policy.
Note: Use the sudo-ldap package if you need LDAP support for sudoers

### Rationale:
sudo supports a plugin architecture for security policies and input/output logging. Third
parties can develop and distribute their own policy and I/O logging plugins to work
seamlessly with the sudo front end. The default security policy is sudoers, which is
configured via the file /etc/sudoers.
The security policy determines what privileges, if any, a user has to run sudo. The policy
may require that users authenticate themselves with a password or another authentication
mechanism. If authentication is required, sudo will exit if the user's password is not
entered within a configurable time limit. This limit is policy-specific.

### Audit:
Verify that sudo in installed.
Run the following command and inspect the output to confirm that sudo is installed:

`# dpkg -s sudo`

## output

```ruby
root@ubuntu-focal:~# dpkg -s sudo
Package: sudo
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 2204
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 1.8.31-1ubuntu1.2
Replaces: sudo-ldap
Depends: libaudit1 (>= 1:2.2.1), libc6 (>= 2.27), libpam0g (>= 0.99.7.1), libselinux1 (>= 2.0.65), libpam-modules, lsb-base
Conflicts: sudo-ldap
Conffiles:
 /etc/pam.d/sudo aa40f755f85bb33c9e79bd537e2979be
 /etc/sudoers edcf6528783ecffd3f248c8089dc298e
 /etc/sudoers.d/README 8d3cf36d1713f40a0ddc38e1b21a51b6
Description: Provide limited super user privileges to specific users
 Sudo is a program designed to allow a sysadmin to give limited root
 privileges to users and log root activity.  The basic philosophy is to give
 as few privileges as possible but still allow people to get their work done.
 .
 This version is built with minimal shared library dependencies, use the
 sudo-ldap package instead if you need LDAP support for sudoers.
Homepage: http://www.sudo.ws/
Original-Maintainer: Bdale Garbee <bdale@gag.com>
root@ubuntu-focal:~#
```

10
### Ensure /var/tmp partition includes the nodev option (Automated)

### Profile Applicability:
- Level 1 - Server
- Level 1 - Workstation

### Description:
The nodev mount option specifies that the filesystem cannot contain special devices.

### Rationale:
Since the /var/tmp filesystem is not intended to support devices, set this option to ensure
that users cannot attempt to create block or character special devices in /var/tmp .

### Audit:
If a /var/tmp partition exists, verify that the nodev option is set.
Run the following command and verify that nothing is returned:

`# findmnt -n /var/tmp | grep -v nodev`

### output

```ruby
root@ubuntu-focal:/home/vagrant# findmnt -n /var/tmp | grep -v nodev
root@ubuntu-focal:/home/vagrant#
```
