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
<img width="1901" height="1000" alt="Screenshot 2025-07-28 124013" src="https://github.com/user-attachments/assets/214500cc-3b71-4501-8fcf-d6c2b5e77189" />

2. Web Server Setup (WebServer1)
Installed Software:
Apache HTTP Server
PHP
Directory: /var/www/html/
Files:
main.php – form to submit user data and file
index.php – optional home or redirect page
Uploads stored and user data inserted into DB
<img width="1820" height="985" alt="Screenshot 2025-07-28 124101" src="https://github.com/user-attachments/assets/7c6c57a3-07bb-4d59-8630-daa52b9c3f14" />

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
<img width="1918" height="1038" alt="Screenshot 2025-07-28 124725" src="https://github.com/user-attachments/assets/d952c51e-53f9-455e-88ba-0bc644f881c3" />

4. SSH Communication (PuTTY)
Used PuTTY to access both WebServer1 and DBServer using:
IP: 192.168.0.210 (Private IP shown)
Port: 22
User: nikhil, then root
SSH commands confirm:
Navigation to /var/www/html
File uploads and DB inserts tested
<img width="811" height="598" alt="Screenshot 2025-07-28 124214" src="https://github.com/user-attachments/assets/a013725a-ee33-44ab-b818-53b23957409d" />
<img width="941" height="706" alt="Screenshot 2025-07-28 124221" src="https://github.com/user-attachments/assets/b5ead588-3c7d-4348-b98d-830e9d9d9c34" />

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
<img width="1885" height="1005" alt="Screenshot 2025-07-28 124957" src="https://github.com/user-attachments/assets/57b047b8-42bd-448c-a8b9-05da4d769946" />

6. Output Verification
You verified:
MySQL DB (udc) → Table (users) has entries
PHP form inserted multiple records
File upload works and is likely stored on server
<img width="767" height="385" alt="Screenshot 2025-07-25 130152" src="https://github.com/user-attachments/assets/6bef2656-bfe1-498b-b728-0992f78bd2c5" />
<img width="1894" height="1037" alt="Screenshot 2025-07-28 125512" src="https://github.com/user-attachments/assets/144dc98a-6eed-4c14-b458-f174f2d3ae44" />


Apache + PHP running on WebServer1
MySQL accessible via root on DBServer
