# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:


## OUTPUT:
![VirtualBox_kali-linux-2024 1-virtualbox-amd64_24_04_2024_10_30sudo](https://github.com/Narasimhan05/Metasploit-for-reconnaissance/assets/132819871/3fc4ceef-b6f2-4e3b-bf7a-0f6b59a1ad78)

Invoke msfconsole:

![VirtualBox_kali-linux-2024 1-virtualbox-amd64_24_04_2024_10_45sudo](https://github.com/Narasimhan05/Metasploit-for-reconnaissance/assets/132819871/f6f5323a-4b5b-41d8-ba4f-ebaa0b302add)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![VirtualBox_kali-linux-2024 1-virtualbox-amd64_24_04_2024_10_46sudo](https://github.com/Narasimhan05/Metasploit-for-reconnaissance/assets/132819871/0ab20b9b-a692-4615-bb74-acffdd36ba92)

Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000

![VirtualBox_kali-linux-2024 1-virtualbox-amd64_24_04_2024_10_43sudo](https://github.com/Narasimhan05/Metasploit-for-reconnaissance/assets/132819871/97f3a1c0-0652-4e27-87b1-2a75f3c8cc10)

use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.
scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24

## OUTPUT:

![VirtualBox_kali-linux-2024 1-virtualbox-amd64_24_04_2024_10_43sudo](https://github.com/Narasimhan05/Metasploit-for-reconnaissance/assets/132819871/651b1213-a265-48bd-ba5e-52f161354c0d)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l

![VirtualBox_kali-linux-2024 1-virtualbox-amd64_24_04_2024_10_41sudo](https://github.com/Narasimhan05/Metasploit-for-reconnaissance/assets/132819871/28b263f8-9082-40e1-a34a-7b3e31773cc4)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit

![VirtualBox_kali-linux-2024 1-virtualbox-amd64_24_04_2024_10_40sudo](https://github.com/Narasimhan05/Metasploit-for-reconnaissance/assets/132819871/d5888aa7-884b-440d-9510-0465c576c409)

The info command provides information regarding a module or platform,

![VirtualBox_kali-linux-2024 1-virtualbox-amd64_24_04_2024_10_37sudo](https://github.com/Narasimhan05/Metasploit-for-reconnaissance/assets/132819871/0894ede0-ee71-4830-81ab-76fd6810f944)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
##MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![VirtualBox_kali-linux-2024 1-virtualbox-amd64_24_04_2024_10_36sudo (2)](https://github.com/Narasimhan05/Metasploit-for-reconnaissance/assets/132819871/372979d9-8b28-4377-a6ee-6e1086b7b01c)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql

![VirtualBox_kali-linux-2024 1-virtualbox-amd64_24_04_2024_10_36sudo](https://github.com/Narasimhan05/Metasploit-for-reconnaissance/assets/132819871/1db5d3e9-7307-402f-88fb-6d37a3f6a986)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version

![VirtualBox_kali-linux-2024 1-virtualbox-amd64_24_04_2024_10_35sudo](https://github.com/Narasimhan05/Metasploit-for-reconnaissance/assets/132819871/786bd048-cb0e-42e1-b7c5-8dc9ffc7d2ab)

Use the set rhosts command to set the parameter and run the module, as follows:

![VirtualBox_kali-linux-2024 1-virtualbox-amd64_24_04_2024_10_33sudo](https://github.com/Narasimhan05/Metasploit-for-reconnaissance/assets/132819871/9f8bf31b-9469-4103-9985-50451dd74a6a)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![VirtualBox_kali-linux-2024 1-virtualbox-amd64_24_04_2024_10_31sudo](https://github.com/Narasimhan05/Metasploit-for-reconnaissance/assets/132819871/6e36b1a7-9252-4965-a24a-ecf1ddbddbc0)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
