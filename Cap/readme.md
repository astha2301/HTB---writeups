# Hack The Box - Cap

## Machine Information

| Field | Details |
|---|---|
| Platform | Hack The Box |
| Machine Name | Cap |
| Difficulty | Easy |
| Operating System | Linux |
| IP Address | `<TARGET_IP>` |
| Main Services | FTP, HTTP, SSH |
| Tools Used | Nmap, Browser, FTP, Wireshark, Linux Terminal |

## Objective

The objective of this machine is to enumerate open ports, explore the web application, identify sensitive information through network traffic, and exploit misconfigured permissions to gain access to the system.

## 1. Reconnaissance

Start by scanning the target machine to identify open ports and running services.

```bash
nmap -sC -sV <TARGET_IP>
```

**What this does:**
- `-sC` – Runs default Nmap scripts.
- `-sV` – Detects service versions.

### Findings

- Port 21 – FTP
- Port 22 – SSH
- Port 80 – HTTP

## 2. Web Enumeration

Open the target IP address in a browser:

```text
http://<TARGET_IP>
```

Explore the web application and inspect the available features.

The application provides network traffic capture functionality, which can be used to investigate packet data.

## 3. Network Traffic Analysis

Explore the available packet capture files and download the relevant capture.

Open the downloaded file using Wireshark.

Filter and inspect the network packets to identify potentially exposed credentials.

## 4. Initial Access

Use the credentials discovered in the packet capture to authenticate to the target machine through SSH.

```bash
ssh <USERNAME>@<TARGET_IP>
```

Enter the discovered password when prompted.

## 5. User Flag

After successfully logging in, navigate to the user's home directory.

```bash
cd ~
ls -la
cat user.txt
```

Retrieve and submit the user flag.

## 6. Privilege Escalation

Enumerate Linux capabilities to identify binaries with potentially dangerous privileges.

```bash
getcap -r / 2>/dev/null
```

Investigate any unusual capabilities and determine whether they can be abused to obtain elevated privileges.

## 7. Root Flag

After obtaining root access, navigate to the root directory.

```bash
cd /root
ls -la
cat root.txt
```

Retrieve and submit the root flag.

## 8. Key Takeaways

- Learned basic network enumeration using Nmap.
- Explored web application functionality.
- Practised downloading and analysing packet captures using Wireshark.
- Understood the risks of exposing credentials in network traffic.
- Learned Linux privilege escalation through capabilities.
- Practised SSH authentication and Linux command-line navigation.

## Conclusion

Cap demonstrates how sensitive information exposed through network traffic and incorrectly configured Linux capabilities can lead to complete system compromise.

**Status:** Machine Completed ✅
