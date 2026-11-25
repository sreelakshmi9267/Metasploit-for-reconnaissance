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

Find out the ip address of the attackers system
## OUTPUT:<img width="1280" height="700" alt="1" src="https://github.com/user-attachments/assets/c52bd38c-579b-4c69-bef5-1b8aac0f6dab" />


Invoke msfconsole:
## OUTPUT:
<img width="1280" height="799" alt="2" src="https://github.com/user-attachments/assets/fd406a02-4d4e-42f3-8061-15903d57ea65" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
<img width="917" height="517" alt="image" src="https://github.com/user-attachments/assets/adb93c64-bd68-401f-a6b8-f86cf582d5c6" />




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="846" height="331" alt="image" src="https://github.com/user-attachments/assets/d45e5ae4-ad9d-41bd-9183-58fa291c55d9" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="858" height="415" alt="image" src="https://github.com/user-attachments/assets/753a9365-abec-4f67-83d7-4d814202076e" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:<img width="1280" height="798" alt="3" src="https://github.com/user-attachments/assets/82955663-e787-4f83-9a16-7ab2ad127a8b" />



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
<img width="957" height="460" alt="image" src="https://github.com/user-attachments/assets/bdf7830b-febb-4ab4-9514-4775422b6015" />



The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:
<img width="845" height="412" alt="image" src="https://github.com/user-attachments/assets/ee9ff07d-18e5-40c5-ac40-c61e240f7bd6" />

<img width="830" height="296" alt="image" src="https://github.com/user-attachments/assets/b9b3ad31-0bf8-4701-b015-4428f6451945" />



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="832" height="210" alt="image" src="https://github.com/user-attachments/assets/ec8e992a-7691-4f46-a9d1-be547fd97f21" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="841" height="350" alt="image" src="https://github.com/user-attachments/assets/3c1158cc-3464-45a2-a060-7ab256389a9b" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
<img width="812" height="283" alt="image" src="https://github.com/user-attachments/assets/e239f639-3dcb-40b2-bb3c-a8ac86bd6819" />




Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:
<img width="658" height="118" alt="image" src="https://github.com/user-attachments/assets/57e8f794-e49a-49dc-bc2e-a90bd5335f8e" />



After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:
<img width="835" height="412" alt="image" src="https://github.com/user-attachments/assets/c5c7b17e-058c-4625-9eae-73df9210baa4" />




set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:
<img width="772" height="190" alt="image" src="https://github.com/user-attachments/assets/01811c84-bedf-4a35-8a05-712390da85c8" />






## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
