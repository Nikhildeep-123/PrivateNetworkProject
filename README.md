# PrivateNetworkProject
A multi-VM private network application using Apache, PHP, and MySQL for secure data storage and file uploads. Built with VirtualBox and SSH-controlled infrastructure.

 1. Virtual Machines Setup (in VirtualBox)
Machines Created:
WebServer1 – hosts the website (frontend + backend)
DBServer – hosts MySQL database
BackupServer – for future backup use (currently saved state)
Configuration:
OS: Red Hat (64-bit)
Memory: ~2 GB per VM
Networking:
Adapter 1: NAT (Internet)
Adapter 2: Bridged/Internal (for communication between VMs)

2. Web Server Setup (WebServer1)
Installed Software:
Apache HTTP Server
PHP
Directory: /var/www/html/
Files:
main.php – form to submit user data and file
index.php – optional home or redirect page
Uploads stored and user data inserted into DB

3. Database Server Setup (DBServer)
Software Installed:
MySQL Server 8.0+

DB Configuration:
sql
Copy
Edit
CREATE DATABASE udc;
USE udc;

CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  age INT NOT NULL,
  country VARCHAR(255),
  degree VARCHAR(100)
);
Sample Query:
sql
Copy
Edit
SELECT * FROM users;
Confirmed working as shown in screenshot.

4. SSH Communication (PuTTY)
Used PuTTY to access both WebServer1 and DBServer using:
IP: 192.168.0.210 (Private IP shown)
Port: 22
User: nikhil, then root
SSH commands confirm:
Navigation to /var/www/html

File uploads and DB inserts tested

5. PHP File Upload and Data Insert (main.php)
Form successfully:
Captures user Name, Age, Country, Degree
Uploads PDF
Inserts values into users table
Displays confirmation
Uploaded file: RESUME_NIKHILDEEP YEMME 81262.pdf
Success message:
User data has been successfully stored in the database.
File uploaded successfully.

6. Output Verification
You verified:
MySQL DB (udc) → Table (users) has entries
PHP form inserted multiple records
File upload works and is likely stored on server
Apache + PHP running on WebServer1
MySQL accessible via root on DBServer
