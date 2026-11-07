HACK THE BOX - FAWN

MACHINE INFORMATION
PLATFORM: hack the box
Machine: Fawn
Difficulty: Very easy
Category: Starting Point

Objective 
To understand basic FTP enumeration, anonymous login and file retrieval

TOOLS USED
nmap
FTP client
Linux terminal

1. ENUMERATION
Started with an nmap scan to identify open ports and running services.
 nmap -sV -sC TARGET_IP

2. FTP Enumeration
Identified FTP running on port 21
checked for anonymous login and explored the available files.

3. File Retrieval
Used the FTP client to access and download the available files.

4. Key learnings
basic network enumeration
FTP service identification
anonymous FTP authentication
Downloading files using FTP

CONCLUSION
This machine helped me understand the basics of FTP enumeration and file transfer as part of my cybersecurity learning journey.





