
# Hack The Box – Dancing

**Platform:** Hack The Box (HTB)  
**Machine:** Dancing  
**Difficulty:** Very Easy  
**Operating System:** Windows  
**Category:** SMB Enumeration

## Overview

Dancing is a beginner-friendly machine on Hack The Box that introduces the basics of SMB (Server Message Block) enumeration and accessing shared network folders.

The objective was to identify available SMB shares, connect to an accessible share, explore its contents, and retrieve the flag.

## Tools Used

- Nmap
- SMBClient
- Linux Terminal

## Steps Performed

### 1. Network Scanning

Used Nmap to scan the target machine and identify open ports and running services.


nmap -sV <TARGET_IP>

**Observation:** SMB-related ports were found open.

### 2. SMB Enumeration

Used `smbclient` to list the available SMB shares on the target machine.


smbclient -L //<TARGET_IP>/


This helped identify the accessible shared folders.

### 3. Connecting to the SMB Share

Connected to the `WorkShares` share using:


smbclient //<TARGET_IP>/WorkShares


Logged in using the available anonymous access.

### 4. Exploring the Share

Used the following commands to navigate and explore the shared directory:


ls
cd <directory>
ls


### 5. Retrieving the Flag

Located the flag file and downloaded it using:


get <flag_filename>

Read the downloaded file using:


cat <flag_filename>


## Key Learnings

- Understanding the basics of SMB protocol.
- Identifying open ports using Nmap.
- Enumerating SMB shares.
- Accessing shares with anonymous authentication.
- Navigating remote directories using SMBClient.
- Downloading files from remote SMB shares.

## Conclusion

Dancing was a great introduction to SMB enumeration and network share exploitation. It helped me understand how improperly configured file-sharing services can expose sensitive information.

