# Linux Lab – CRACKING PASSWORD HASHES USING JOHN THE RIPPER
## Objective

The objective of this script is to block incoming network traffic from a list of specified IP addresses using the iptables firewall in Linux. It automates the process of applying IP-based traffic restrictions for network security purposes.

### Job Skills Learned

- Linux System Administration
- Managing firewall rules using iptables.
- Bash Shell Scripting
- Using loops and conditional commands.
- Network Security and Access Control
- Automation and Efficiency


### Tools Used

- Linux Terminal Command Line Interface (CLI)
- Bash Shell
- iptables (Firewall)
- Networking Commands: ping, ifconfig
- VMware Tools: Linux VM

*Ref: Diagram:



### STEPS

# Installing JTR
`apt install john`
![image](https://github.com/user-attachments/assets/dc30b732-f353-4fba-ad23-8fbfcd01c733)
 
 
# combining /etc/passwd and /etc/shadow in a single file
`unshadow /etc/passwd /etc/shadow > unshadowed.txt`
![image](https://github.com/user-attachments/assets/0121c105-aad7-4e14-9529-5b38ff664209)
 
 
# Cracking in single mode
`john -single --format=crypt unshadowed.txt --format=crypt`
![image](https://github.com/user-attachments/assets/b6a3136b-4519-4132-830b-b97766192582)
 
 
# brute-force and dictionary attack
![image](https://github.com/user-attachments/assets/6252edb6-5661-41a6-9e4e-5756934cf1f7)
 
 
# dictionary files:
# /usr/share/dict  
# /usr/share/metasploit-framework/data/wordlists # -> on Kali Linux
 
# showing cracked hashes  (~/.john/john.pot)
`john --show unshadowed.txt`
 ![image](https://github.com/user-attachments/assets/7024692c-b26e-43b1-ad0e-d712a4adf6b6)

 
# to continue an interrupted (ctrl+c) session, run  in the same directory:
`john -restore`
![image](https://github.com/user-attachments/assets/4931a2a6-f393-432d-b6a0-1b0b8d310609)
 

 
# Cracking only accounts with specific shells (valid shells) 
![image](https://github.com/user-attachments/assets/0a8bf8cd-a2fb-45fd-ba7a-8a1dea82a0fb)
 

# Cracking only some accounts
![image](https://github.com/user-attachments/assets/6e0047da-c326-444b-8cc3-af891c881b88)
  
# Cracking in incremental mode (/etc/john/john.conf)
`john --incremental unshadowed.txt --format=crypt`
![image](https://github.com/user-attachments/assets/a5726004-b541-44b4-bc2a-a54e9f0425d7)
 
 
# Eliminate duplicates from a wordlist (if any)
`john --wordlist=mydict.txt --stdout | unique mydictionary.txt`
