![etex55](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/651a04e0-fe98-432c-aece-1f87beafe929)# Metasploit-for-reconnaissance
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
## PROGRAM:

Find out the ip address of the attackers system

## OUTPUT:

![etex51](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/3f2fe54c-c76c-46e7-8deb-875e1f027682)

## Invoke msfconsole:


## OUTPUT:
![etex52](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/25a9eac7-4642-417f-b1a4-8a30ae3a5425)



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:

![etex53](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/a77fb0e7-1aea-4b7e-92f1-2eab6afd309e)

## Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:

![etex54](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/9e9cf8f4-a0ca-49b6-9271-dcb69331b373)

## step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24

## OUTPUT:

![etex55](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/219801dd-34cb-4d1e-bdcd-43e020540d2c)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls 


## OUTPUT:
![etex56](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/2c65b89b-6cef-45a7-a845-3f4541411d06)


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit

## OUTPUT:
![etex57](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/f2d76946-1251-456b-9dec-ab42525777c0)


The info command provides information regarding a module or platform,

## OUTPUT:
![etex58](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/e44a4336-1bbc-4e13-83be-e0f0cf5f61b4)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
![etex59](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/13e952ad-6ce1-4e5d-960b-772f972c5cdd)


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql

## OUTPUT:
![etex510](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/7ea1951c-f0f4-49cc-a1a3-55a8b8f41779)


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version

## OUTPUT:
![etex511](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/84a8f32b-4246-40c8-adb4-21a629dfaad3)


Use the set rhosts command to set the parameter and run the module, as follows:

## OUTPUT:

![etex512](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/9248b1d5-4e0e-4cc3-89be-44d22192dcb5)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

## OUTPUT:
![etex513](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/e35fbef4-d419-4da0-bd85-46ff10d14176)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true

## OUTPUT:

![etex514](https://github.com/MDINESH220305/Metasploit-for-reconnaissance/assets/162429215/fc157f51-aad2-428d-bbe3-543acf421134)

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
