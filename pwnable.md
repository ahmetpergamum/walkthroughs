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

From the [read function man page](https://linux.die.net/man/3/read);

>The read() function shall attempt to read nbyte (32) bytes from the file associated with the open file descriptor, fd, into the buffer pointed to by buf.

From the [wiki](http://www.wikizero.info/index.php?q=aHR0cHM6Ly9lbi53aWtpcGVkaWEub3JnL3dpa2kvRmlsZV9kZXNjcmlwdG9y) pages of file desciptor;

>A file descriptor is a non-negative integer, generally represented in the C programming language as the type int (negative values being reserved to indicate "no value" or an error condition).

Provide numbers equal or greater than `4660 (0x1234)` for a valid file descriptor.

Both `4660 and 4661` works fine.

And provide `LETMEWIN` string to pass the `strcmp()` test.

```
./fd.c 4660
LETMEWIN
good job :)
mommy! I think I know what a file descriptor is!!
```
