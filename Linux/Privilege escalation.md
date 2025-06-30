## Linux Privilege Escalation Notes

Using the `linpeas.sh` script will reveal the vulnerable point in 90% of cases.  
If it misses, manually checking the following can be very helpful:

- `/opt` directory – Check for scripts or binaries with weak permissions  
- `/var/backups` – May contain old versions of sensitive files or credentials  
- Kernel and OS version – Check for known local privilege escalation vulnerabilities  
- Binaries with the `SetUID` bit set  
- Hidden cron jobs with sudo privileges (can be discovered using the `pspy` binary)  
- Environment variables – May leak sensitive data or paths  
- Hidden files inside the user's home directory  
- Web services running locally – May be hosted outside the usual `/var/www/html` directory  
