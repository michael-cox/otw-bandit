# OverTheWire Bandit Project

## Student Information

* Student name: **enter name here**
* NetId: **enter NetId here**


## Project Description

In this project, you will be complete the Bandit challenges at <https://overthewire.org/wargames/bandit/>. For each challenge, you will complete the following worksheet describing:
1. The credentials found in the challenge.
2. How you solved the challenge. Include the commands and scripts you used to retrieve the credentials. You can use the linux command `history` to view commands used in the current session.
3. What sins (as found in the *24 Deadly Sins* book) are evidenced in the challenge.
4. How those sins should be addressed to address your exploit.

In the workshop, the challenges are named based on the username used to login to the shell for that challenge. For example, the challenge labeled "Natas 10" will be logged into with the username natas10, and the solution will be the credentials for the user natas11.

You can find a basic guide for markdown formatting [here](https://www.markdownguide.org/basic-syntax/). In particular, note the [code section](https://www.markdownguide.org/basic-syntax/#code) which should be used to annotate any code or commands used in your writeup.

## Hints
There are hints for each challenge on the [Bandit](https://overthewire.org/wargames/bandit/) webpage.

Below are several additional hints:
* Bandit 24: The netcat server dies if sent too much input. Limit how much content you send per connection.
* Bandit 25: This level is only finished once you have the password for bandit26. The ssh key along is insufficient. Also, how does `vi` factor into all of this?
* Bandit 28–30: Core `git` features include commits, branches, and tags.
* Bandit 32: `sh` has access to argc and argv.


## Challenges

---
### Bandit 00

#### Credentials
`bandit0:bandit0`

#### How you passed the challenge
* `ssh bandit0@bandit.labs.overthewire.org -p 2220`

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)

#### How could those sins be mitigated
* Do not place passwords or other sensitive information on a public website.


---
### Bandit 01

#### Credentials
`bandit1:boJ9jbbUNNfktd78OOpsqOltutMc3MY1`

#### How you passed the challenge
* `cat readme`

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)

#### How could those sins be mitigated
* Do not place passwords in plaintext
* Do not place sensitive information in files readable to unauthorized users



---
### Bandit 02

#### Credentials
`bandit2:CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9`

#### How you passed the challenge
* `cat ./-`

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)

#### How could those sins be mitigated
* Do not place passwords in plaintext
* Do not place sensitive information in files readable to unauthorized users
* Do not rely on filename obscurity to hide the file's contents



---
### Bandit 03

#### Credentials
`bandit3:UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK`

#### How you passed the challenge
* `cat spaces\ in\ this\ filename`

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)

#### How could those sins be mitigated
* Do not place passwords in plaintext
* Do not place sensitive information in files readable to unauthorized users
* Do not rely on filename obscurity to hide the file's contents



---
### Bandit 04

#### Credentials
`bandit4:pIwrPrtPN36QITSp3EQaw936yaFoFgAB`

#### How you passed the challenge
```sh
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -a
.  ..  .hidden
bandit3@bandit:~/inhere$ cat .hidden
<password>
```

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)

#### How could those sins be mitigated
* Do not place passwords in plaintext
* Do not place sensitive information in files readable to unauthorized users
* Do not rely on "hidden" dot files to hide sensitive information



---
### Bandit 05

#### Credentials
`bandit5:koReBOKuIDDepwhWk7jZC0RTdopnAYKh`

#### How you passed the challenge
```sh
bandit4@bandit:~/inhere$ for i in *; do echo $i; strings ./$i; done
-file00
-file01
-file02
-file03
!TQO
-file04
-file05
-file06
-file07
<password>
-file08
```

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)

#### How could those sins be mitigated
* Do not place passwords in plaintext
* Do not place sensitive information in files readable to unauthorized users
* Do not rely on filename obscurity/dummy files to hide the contents of a file



---
### Bandit 06

#### Credentials
`bandit6:DXjZPULLxYr17uwoI01bNLQbtFemEgo7`

#### How you passed the challenge
```sh
bandit5@bandit:~$ cd inhere/
bandit5@bandit:~/inhere$ find . -type f -size 1033c ! -executable -exec file {} \; | grep ASCII
./maybehere07/.file2: ASCII text, with very long lines
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
<password>
```

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)

#### How could those sins be mitigated
* Do not place passwords in plaintext
* Do not place sensitive information in files readable to unauthorized users
* Do not rely on dummy files to hide the contents of a file



---
### Bandit 07

#### Credentials
`bandit7:HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs`

#### How you passed the challenge
```sh
bandit6@bandit:~$ find / -group bandit6 -user bandit7 -size 33c
...
/var/lib/dpkg/info/bandit7.password
...
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
<password>
```


#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)

#### How could those sins be mitigated
* Do not place passwords in plaintext
* Do not place sensitive information in files readable to unauthorized users
* Do not rely on obscure location to hide sensitive information



---
### Bandit 08

#### Credentials
`bandit8:cvX2JJa4CFALtqS87jk27qwqGhBM9plV`

#### How you passed the challenge
```sh
bandit7@bandit:~$ strings data.txt  | grep millionth
millionth	<password>
```

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)

#### How could those sins be mitigated
* Do not place passwords in plaintext
* Do not place sensitive information in files readable to unauthorized users
* Do not rely on obscure surrounding data to hide sensitive information



---
### Bandit 09

#### Credentials
`bandit9:UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR`

#### How you passed the challenge
`sort -n data.txt | uniq -u`

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)

#### How could those sins be mitigated
* Do not place passwords in plaintext
* Do not place sensitive information in files readable to unauthorized users
* Do not rely on obscure surrounding data to hide sensitive information



---
### Bandit 10

#### Credentials
`bandit10:truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk`

#### How you passed the challenge
* `strings data.txt | grep '=='`
* try the most likely password until success

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)

#### How could those sins be mitigated
* Do not place passwords in plaintext
* Do not place sensitive information in files readable to unauthorized users
* Do not rely on obscure surrounding data to hide sensitive information



---
### Bandit 11

#### Credentials
`bandit11:IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR`

#### How you passed the challenge
* `base64 -d data.txt`

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-257: Storing Passwords in a Recoverable Format](https://cwe.mitre.org/data/definitions/257.html)
* [CWE-261: Weak Encoding for Password](https://cwe.mitre.org/data/definitions/261.html)

#### How could those sins be mitigated
* Use strong secure hashes for passwords
* Do not place sensitive information in files readable to unauthorized users



---
### Bandit 12

#### Credentials
`bandit12:5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu`

#### How you passed the challenge
* `cat data.txt`
* Use a caesar's cipher utility I built to decipher ascii characters by 13

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-257: Storing Passwords in a Recoverable Format](https://cwe.mitre.org/data/definitions/257.html)
* [CWE-261: Weak Encoding for Password](https://cwe.mitre.org/data/definitions/261.html)

#### How could those sins be mitigated
* Use strong secure hashes for passwords
* Do not place sensitive information in files readable to unauthorized users



---
### Bandit 13

#### Credentials
`bandit13:8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL`

#### How you passed the challenge
```sh
bandit12@bandit:/tmp/mcox$ xxd -r data.txt.bac data.txt
bandit12@bandit:/tmp/mcox$ file data.txt
data.txt: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/mcox$ mv data.txt data.gz
bandit12@bandit:/tmp/mcox$ gunzip data.gz
bandit12@bandit:/tmp/mcox$ file data
data: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/mcox$ mv data data.bz2
bandit12@bandit:/tmp/mcox$ bunzip2 data.bz2
bandit12@bandit:/tmp/mcox$ mv data data.gz
bandit12@bandit:/tmp/mcox$ gunzip data.gz
bandit12@bandit:/tmp/mcox$ file data
data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/mcox$ tar -xvf data.tar
data5.bin
bandit12@bandit:/tmp/mcox$ file data5.bin 
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/mcox$ tar -xvf data5.bin
data6.bin
bandit12@bandit:/tmp/mcox$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/mcox$ mv data6.bin data6.bz2
bandit12@bandit:/tmp/mcox$ bunzip2 data6.bz2 
bandit12@bandit:/tmp/mcox$ ls
data5.bin  data6  data.tar  data.txt.bac
bandit12@bandit:/tmp/mcox$ file data6
data6: POSIX tar archive (GNU)
bandit12@bandit:/tmp/mcox$ tar -xvf data6
data8.bin
bandit12@bandit:/tmp/mcox$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/mcox$ mv data8.bin data8.gz
bandit12@bandit:/tmp/mcox$ gunzip data8.gz 
bandit12@bandit:/tmp/mcox$ ls
data5.bin  data6  data8  data.tar  data.txt.bac
bandit12@bandit:/tmp/mcox$ file data8
data8: ASCII text
bandit12@bandit:/tmp/mcox$ cat data8
The password is <password>
```

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-257: Storing Passwords in a Recoverable Format](https://cwe.mitre.org/data/definitions/257.html)
* [CWE-261: Weak Encoding for Password](https://cwe.mitre.org/data/definitions/261.html)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)


#### How could those sins be mitigated
* Use strong secure hashes for passwords
* Do not place sensitive information in files readable to unauthorized users
* Do not rely on obscurity by repeated compression



---
### Bandit 14

#### Credentials
`bandit14:4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e`

#### How you passed the challenge
```sh
> scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
...
> chmod 600 sshkey.private
> ssh-add sshkey.private
> ssh bandit14@bandit.labs.overthewire.org -p 2220 
> cat /etc/bandit_pass/bandit14 
<password>
```


#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-732: Incorrect Permission Assignment for Critical Resource](https://cwe.mitre.org/data/definitions/732.html)

#### How could those sins be mitigated
* Securely store private keys with user permissions
* Securely hash passwords
* Don't store passwords in cleartext



---
### Bandit 15

#### Credentials
`bandit15:BfMYroe26WYalil77FoDi9qh59eK5xNr`

#### How you passed the challenge
```sh
bandit14@bandit:~$ nc localhost 30000
<input bandit14's password>
Correct!
<new password>
```

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-319: Cleartext Transmission of Sensitive Information](https://cwe.mitre.org/data/definitions/319.html)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)

#### How could those sins be mitigated
* Do not implement privilege escalation on a system
* Securely encrypt all passwords transmitted through exposed channels
* Don't rely on obscurity of passing passwords through sockets on localhost



---
### Bandit 16

#### Credentials
`bandit15:cluFn7wTiGryunymYOu4RcffSxQluehd`

#### How you passed the challenge
```sh
bandit14@bandit:/tmp/dir$ socat - OPENSSL:localhost:30001,verify=0
<input old password>
Correct!
<new password>
```

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)

#### How could those sins be mitigated
* Do not implement privilege escalation on a system
* Don't rely on obscurity of passing passwords through sockets on localhost



---
### Bandit 17

#### Credentials
`bandit17:xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn`

#### How you passed the challenge
```sh
# on remote host
bandit16@bandit:~$ nmap -p 31000-32000 localhost

Starting Nmap 7.40 ( https://nmap.org ) at 2021-03-27 23:20 CET
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00030s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown
...
bandit16@bandit:~$ openssl s_client -connect localhost:31790
CONNECTED(00000003)
depth=0 CN = localhost
...
bandit16@bandit:~$ socat - OPENSSL:localhost:31790,verify=0 
cluFn7wTiGryunymYOu4RcffSxQluehd
Correct!
-----BEGIN RSA PRIVATE KEY-----
...

# on local host
> ssh-add priv
Identity added: priv (priv)
> ssh bandit17@bandit.labs.overthewire.org -p 2220

# back on remote as bandit17
bandit17@bandit:~$ cat /etc/bandit_pass/bandit17 
<password>
```

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)

#### How could those sins be mitigated
* Do not implement privilege escalation on a system
* Don't rely on obscurity of passing passwords through sockets on localhost
* Don't rely on obscurity of having several different "dummy" sockets


---
### Bandit 18

#### Credentials
`bandit18:kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd`

#### How you passed the challenge
```sh
bandit17@bandit:~$ diff -y passwords.new passwords.old
Q5k9tXSLUPHv282xtRThOvNRPR9X4Tvz				Q5k9tXSLUPHv282xtRThOvNRPR9X4Tvz
vEYciPARcb7gHg33yA1iDL7GVTipg3Zg				vEYciPARcb7gHg33yA1iDL7GVTipg3Zg
ficqxGmpiJeT79Qa5E1el2XeIFF4cKgN				ficqxGmpiJeT79Qa5E1el2XeIFF4cKgN
2z0gnshvn6CbwBMdiQxYRmyiwA4Eo7Y2				2z0gnshvn6CbwBMdiQxYRmyiwA4Eo7Y2
FgZhGJsdwY2aTkDEb7FoxJ0YUy6J1cGR				FgZhGJsdwY2aTkDEb7FoxJ0YUy6J1cGR
Ix2a92Aq8dGCMOat95FYulOOx6MTHfEZ				Ix2a92Aq8dGCMOat95FYulOOx6MTHfEZ
...
<password>                                    |	...
...
```

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-732: Incorrect Permission Assignment for Critical Resource](https://cwe.mitre.org/data/definitions/732.html)

#### How could those sins be mitigated
* Do not store passwords in cleartext
* Implement good permissions/access controls on files containing secret information


---
### Bandit 19

#### Credentials
`bandit19:IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x`

#### How you passed the challenge
`ssh bandit18@bandit.labs.overthewire.org -p 2220 'cat readme'`

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)
* [CWE-732: Incorrect Permission Assignment for Critical Resource](https://cwe.mitre.org/data/definitions/732.html)

#### How could those sins be mitigated
* Do not store passwords in cleartext
* Implement good permissions/access controls on files containing secret information
* Do not rely on obscurity through scripts that immediately logout the user



---
### Bandit 20

#### Credentials
`bandit20:GbKksEFF4yrVs6il55v6gwY5aVje5f0j`

#### How you passed the challenge
* `./bandit20-do cat /etc/bandit_pass/bandit20`

#### What sins are evidenced in this challenge
* [CWE-272: Least Privilege Violation](https://cwe.mitre.org/data/definitions/272.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)

#### How could those sins be mitigated
* Do not use the setuid bit unless absolutely necessary
* Do not store passwords in cleartext



---
### Bandit 21

#### Credentials
`bandit21:gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr`

#### How you passed the challenge
```sh
bandit20@bandit:~$ nc -nlvp 40002&
[2] 26928
listening on [any] 40002 ...
bandit20@bandit:~$ ./suconnect 40002 &
connect to [127.0.0.1] from (UNKNOWN) [127.0.0.1] 39726
bandit20@bandit:~$ fg 2
nc -nlvp 40002
<input old password>
Read: <old password>
Password matches, sending next password
<new password>
```

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-272: Least Privilege Violation](https://cwe.mitre.org/data/definitions/272.html)
* [CWE-319: Cleartext Transmission of Sensitive Information](https://cwe.mitre.org/data/definitions/319.html)

#### How could those sins be mitigated
* Do not implement privilege escalation
* Do not use the setuid bit unless absolutely necessary
* Securely encrypt passwords before transmissiting over insecure channels



---
### Bandit 22

#### Credentials
`bandit22:Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI`

#### How you passed the challenge
```sh
bandit21@bandit:~$ ls /etc/cron.d
cronjob_bandit15_root  cronjob_bandit17_root  cronjob_bandit22  cronjob_bandit23  cronjob_bandit24  cronjob_bandit25_root
bandit21@bandit:~$ cat /usr/bin/cronjob_bandit22.sh 
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
bandit21@bandit:~$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
<password>
```

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)


#### How could those sins be mitigated
* Do not leak sensitive information in world readable files
* Securely hash passwords
* Do not conceal files containing sensitive information with obscure filenames


---
### Bandit 23

#### Credentials
`bandit23:jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n`

#### How you passed the challenge
```sh
bandit22@bandit:~$ cat /etc/cron.d/cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
bandit22@bandit:~$ cat /usr/bin/cronjob_bandit23.sh 
...
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
...
cat /etc/bandit_pass/$myname > /tmp/$mytarget

bandit22@bandit:~$ cat /tmp/`echo I am user bandit23 | md5sum | cut -d ' ' -f 1`
<password>
```

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)

#### How could those sins be mitigated
* Do not leak sensitive information in world readable files
* Securely hash passwords
* Do not conceal files containing sensitive information with obscure filenames



---
### Bandit 24

#### Credentials
`bandit24:UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ`

#### How you passed the challenge
```sh
bandit23@bandit:~$ cat /etc/cron.d/cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh
# script that arbitrarily executes scripts in /var/spool/bandit24
bandit23@bandit:/tmp/test1254$ ls -ld /var/spool/bandit24
drwxrwx-wx 9 root bandit24 4096 Mar 28 00:22 /var/spool/bandit24    # this directory is writable by anyone

# make a script containing the following
#!/bin/bash

cat /etc/bandit_pass/bandit24 >> /tmp/badfile32

# make that file
bandit23@bandit:/tmp/test1254$ touch /tmp/badfile32
bandit23@bandit:/tmp/test1254$ chmod 777 /tmp/badfile32
bandit23@bandit:/tmp/test1254$ chmod 777 script
bandit23@bandit:/tmp/test1254$ cp script /var/spool/bandit24
# wait a minute
bandit23@bandit:/tmp/test1254$ cat /tmp/badfile32
<password>
```

#### What sins are evidenced in this challenge
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-732: Incorrect Permission Assignment for Critical Resource](https://cwe.mitre.org/data/definitions/732.html)
* [CWE-829: Inclusion of Functionality from Untrusted Control Sphere](https://cwe.mitre.org/data/definitions/829.html)

#### How could those sins be mitigated
* Do not implement arbitrary code execution
* Assign strong permissions to sensitive directories
* Securely hash passwords.



---
### Bandit 25

#### Credentials
`bandit25:uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG`

#### How you passed the challenge
```sh
bandit24@bandit:/tmp/mtest$ for i in {0000..9999}; do  
> echo "<password> $i" >> input
> done
bandit24@bandit:/tmp/mtest$ cat file | nc localhost 30002 > output
bandit24@bandit:/tmp/mtest$ grep -v Wrong output 
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Correct!
The password of user bandit25 is <password>
```

#### What sins are evidenced in this challenge
* [CWE-200: Exposure of Sensitive Information to an Unauthorized Actor](https://cwe.mitre.org/data/definitions/200.html)
* [CWE-307: Improper Restriction of Excessive Authentication Attempts](https://cwe.mitre.org/data/definitions/307.html)
* [CWE-319: Cleartext Transmission of Sensitive Information](https://cwe.mitre.org/data/definitions/319.html)
* [CWE-521: Weak Password Requirements](https://cwe.mitre.org/data/definitions/521.html)

#### How could those sins be mitigated
* Do not implement privilege escalation
* Require better passwords (see CWE-521)
* Securely encrypt passwords
* Implement login attempt protection measures



---
### Bandit 26

#### Credentials
`bandit26:5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z `

#### How you passed the challenge
* Load the ssh key from bandit25 to login to bandit26
* Shrink my terminal to make more pause on login
* Press `v` to enter vi mode
* Execute `:e /etc/bandit_pass/bandit26` to get credential

#### What sins are evidenced in this challenge
* [CWE-656: Reliance on Security Through Obscurity](https://cwe.mitre.org/data/definitions/656.html)
* [CWE-829: Inclusion of Functionality from Untrusted Control Sphere](https://cwe.mitre.org/data/definitions/829.html)

#### How could those sins be mitigated
* Don't rely on an obscure shell to enforce security, use a restricted shell



---
### Bandit 27

#### Credentials
`bandit27:3ba3118a22e93127a4ed485be72ef5ea`

#### How you passed the challenge
** Steps here **
* While in vim-mode
* `set shell=/bin/bash`
* `:shell`
* `./bandit27-do cat /etc/bandit_pass/bandit27`

#### What sins are evidenced in this challenge
* [CWE-272: Least Privilege Violation](https://cwe.mitre.org/data/definitions/272.html)
* [CWE-313: Cleartext Storage in a File or on Disk](https://cwe.mitre.org/data/definitions/313.htm)
* [CWE-829: Inclusion of Functionality from Untrusted Control Sphere](https://cwe.mitre.org/data/definitions/829.html)

#### How could those sins be mitigated
* Do not rely on an obscure shell to restrict access
* Do not use the setuid bit unless absolutely necessary
* Do not store passwords in cleartext



---
### Bandit 28

#### Credentials
`bandit28:0ef186ac70e04ea33b4c1853d2526fa2`

#### How you passed the challenge
```sh
bandit27@bandit:/tmp$ mkdir b27git
bandit27@bandit:/tmp$ cd !$
cd b27git
bandit27@bandit:/tmp/b27git$ git clone git@localhost:bandit27-git/repo
bandit27@bandit:/tmp/b27git$ cd repo
bandit27@bandit:/tmp/b27git/repo$ cat README 
The password to the next level is: <password>
```

#### What sins are evidenced in this challenge
* [CWE-312: Cleartext Storage of Sensitive Information](https://cwe.mitre.org/data/definitions/312.html)

#### How could those sins be mitigated
* Don't store sensitive information in version control



---
### Bandit 29

#### Credentials
`bandit29:bbc96594b4e001778eee9975372716b2`

#### How you passed the challenge
```sh
bandit28@bandit:/tmp/b28test$ git clone bandit28-git@localhost:/home/bandit28-git/repo
bandit28@bandit:/tmp/b28test/repo$ git log
bandit28@bandit:/tmp/b28test/repo$ git checkout c086d11a00c0648d095d04c089786efef5e01264
bandit28@bandit:/tmp/b28test/repo$ cat README.md
...
<password>
...
```

#### What sins are evidenced in this challenge
* [CWE-312: Cleartext Storage of Sensitive Information](https://cwe.mitre.org/data/definitions/312.html)

#### How could those sins be mitigated
* Don't store sensitive information in version control



---
### Bandit 30

#### Credentials
`bandit30:5b90576bedb2cc04c86a9e924ce42faf`

#### How you passed the challenge
```sh
bandit29@bandit:/tmp/b29test$ git clone bandit29-git@localhost:/home/bandit29-git/repo
bandit29@bandit:/tmp/b29test/repo$ git branch -a
bandit29@bandit:/tmp/b29test/repo$ git checkout dev
bandit29@bandit:/tmp/b29test/repo$ cat README.md 
```

#### What sins are evidenced in this challenge
* [CWE-312: Cleartext Storage of Sensitive Information](https://cwe.mitre.org/data/definitions/312.html)

#### How could those sins be mitigated
* Don't store sensitive information in version control



---
### Bandit 31

#### Credentials
`bandit31:47e603bb428404d265f59c42920d81e5`

#### How you passed the challenge
```sh
bandit30@bandit:/tmp/b30test$ git clone bandit30-git@localhost:/home/bandit30-git/repo
...
bandit30@bandit:/tmp/b30test/repo$ git tag
secret
bandit30@bandit:/tmp/b30test/repo$ git show secret
```

#### What sins are evidenced in this challenge
* [CWE-312: Cleartext Storage of Sensitive Information](https://cwe.mitre.org/data/definitions/312.html)

#### How could those sins be mitigated
* Don't store sensitive information in version control



---
### Bandit 32

#### Credentials
`bandit32:56a9bf19c63d650ce78e6ec0354ee45e`

#### How you passed the challenge
```sh
bandit31@bandit:/tmp/b31test$ git clone bandit31-git@localhost:/home/bandit31-git/repo
Cloning into 'repo'...
bandit31@bandit:/tmp/b31test/repo$ cat README.md 
bandit31@bandit:/tmp/b31test/repo$ git rm .gitignore 
rm '.gitignore'
bandit31@bandit:/tmp/b31test/repo$ echo "May I come in?" > key.txt
bandit31@bandit:/tmp/b31test/repo$ git branch
* master
bandit31@bandit:/tmp/b31test/repo$ git add key.txt 
bandit31@bandit:/tmp/b31test/repo$ git commit -m 'dummy commit'
...
bandit31@bandit:/tmp/b31test/repo$ git push -u origin master
...
<password>
...
```

#### What sins are evidenced in this challenge
* [CWE-312: Cleartext Storage of Sensitive Information](https://cwe.mitre.org/data/definitions/312.html)

#### How could those sins be mitigated
* Don't store sensitive information in version control


