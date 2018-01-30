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
...
rioGegei8m
...
```
### leviathan2
There is a binary with suid bit is set and it checks the password,
I googled about priviledge escalation with suid binaries for about an hour or two but nothing to show for it.
Finally I found this [geekstuff/reverse_engineering_tools](https://www.thegeekstuff.com/2012/03/reverse-engineering-tools/)
I tried the `ltrace` and found that *check* program compares the user input with *strcmp* function
```
$ ltrace ./check
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

### leviathan3
There is a suid program named, it prints files with checking permissions.
Examine the program w,th `ltrace`
```
$ ltrace ./printfile /etc/hostname
```
It checks the access permissions with `access()` function but there is a vulnerability about the `""`
while calling `/bin/cat` program.

Make a file with blank in its name and make a symbolic link with one of its parts
```
$ mkdir /tmp/xx
$ cd /tmp/xx
$ touch test\ pass3
$ ln -s /etc/leviathan_pass/levitahan3 pass3
```
Test the program
```
$ ~/printfile "test pass3"
Ahdiemoo1j
```

### leviathan4

There is a suid program check it out.
```
$ ./level3
Enter the password> aaaaa
bzzzzzzzzap. WRONG
```
Examine with ltrace
```
$ ltrace ./level3
...
strcmp("\n", "snlprintf\n")
...
```
`strcmp()` compares `snlprintf` with user input.
Use it as password;
```
$ ./level3
Enter the password> snlprintf
[You've got shell]!
$ whoami
leviathan4
$ cat /etc/leviathan_pass/leviathan4
vuH0coox6m
```

