## krypton wargame
### krypton1
Connect krypton1 with ssh after decoding base64 encoded text
```
$ echo S1JZUFRPTklTR1JFQVQ | base64 -d
KRYPTONISGREAT
$ ssh krypton.labs.overthewire.org -p 2222 -l krypton1
```
### krypton2
The password is encrypted with simple rotationi rot-13
If rot-13 is tried with `tr` first it worked.

```
cd /krypton/krypton1
cat krypton2 | tr 'A-Za-z' 'N-ZA-Mn-za-m'
LEVEL TWO PASSWORD ROTTEN
```
### krypton3
The password is encrypted with ceaser cipher but key file is not allowed to read
The key should be determined with a test file
```
$ mkdir /tmp/xx/
$ cd /tmp/xx
$ ln -s /krypton/krypton2/keyfile.dat
$ echo AAAAA > test.txt
$ /krypton/krypton2/encrypt test.txt
$ cat ciphertext
MMMMM
```
The key is 12 so the substitution cipher is rot-12

Encrypt the encrypted password again after that rotate by 2

```
/krypton/krypton2/encrypt /krypton/krypton2/krypton3
cat ciphertext | tr 'A-Za-z' 'C-ZA-Bc-za-b'
CAESARISEASY
```
