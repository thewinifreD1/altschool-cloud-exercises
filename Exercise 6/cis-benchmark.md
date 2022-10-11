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


Ensure noexec option set on /tmp partition (Automated)
Profile Applicability:
 Level 1 - Server
 Level 1 - Workstation
Description:
The noexec mount option specifies that the filesystem cannot contain executable binaries.
Rationale:
Since the /tmp filesystem is only intended for temporary file storage, set this option to
ensure that users cannot run executable binaries from /tmp.
Audit:
If a /tmp partition exists, verify that the noexec option is set.
Run the following command and verify that nothing is returned:
# findmnt -n /tmp | grep -v noexec
