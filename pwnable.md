# pwnable.kr walktrough
[pwnable.kr](http://pwnable.kr/play.php)
### fd

Connect the server;
```
ssh fd@pwnable.kr -p2222
password is guest
```
There are three files in home directory
```
fd@ubuntu:~$ ls -al
total 40
drwxr-x---  5 root   fd   4096 Oct 26  2016 .
drwxr-xr-x 87 root   root 4096 Dec 27 23:17 ..
d---------  2 root   root 4096 Jun 12  2014 .bash_history
-rw-------  1 root   root  128 Oct 26  2016 .gdb_history
dr-xr-xr-x  2 root   root 4096 Dec 19  2016 .irssi
drwxr-xr-x  2 root   root 4096 Oct 23  2016 .pwntools-cache
-r-sr-x---  1 fd_pwn fd   7322 Jun 11  2014 fd
-rw-r--r--  1 root   root  418 Jun 11  2014 fd.c
-r--r-----  1 fd_pwn root   50 Jun 11  2014 flag
```
`fd` suid program

`fd.c`  source code

`flag` target file

Anlayze the source code,

![Image of fd.c ](https://github.com/ahmetpergamum/walkthroughs/blob/master/images/fdc.png)
