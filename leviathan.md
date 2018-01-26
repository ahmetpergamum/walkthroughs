## leviathan wargame
### leviathan0
Connect leviathan0 with ssh
```
$ ssh leviathan.labs.overthewire.org -p 2223 -l leviathan0
leviathan0
```
### leviathan1
Open the *.bookmarks.html* file in *.backup* directory and look for *pass* string
```
$ grep pass .backup/bookmarks.html
rioGegei8m
```
### leviathan2
There is a binary with suid bit is set and it checks the password,
I googled about priviledge escalation with suid binaries for about an hour or two but nothing to show for it.
Finally I found this [geekstuff/reverse_engineering_tools](https://www.thegeekstuff.com/2012/03/reverse-engineering-tools/)
I tried the `ltrace` and found that *check* program compares the user input with *strcmp* function
```
ltrace ./check
...
strcmp("asdf\n", "sex")
...
```
After providing the correct password suid program spawn a shell with priviledged rights
```
$ id
uid=12002(leviathan2) gid=12001(leviathan1) groups=12001(leviathan1)
$ cat /etc/leviathan_pass/leviathan2
ougahZi8Ta
```
