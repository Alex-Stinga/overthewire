# overthewire

Level 0
-------------
STATEMENT

Level Goal
The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. 
The username is bandit0 and the password is **bandit0**. Once logged in, go to the Level 1 page to find out how to beat Level 1.

Commands you may need to solve this level
ssh

Helpful Reading Material
Secure Shell (SSH) on Wikipedia
How to use SSH on wikiHow

SOLVE

> ssh bandit0@bandit.labs.overthewire.org -p 2220



Level 1
-------------
STATEMENT

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

SOLVE

> cat readme



The password we got: 



Level 2
-------------
STATEMENT

The password for the next level is stored in a file called - located in the home directory

Commands you may need to solve this level
ls, cd, cat, file, du, find

SOLVE

> ssh bandit1@bandit.labs.overthewire.org -p 2220
> ls -alh
There is a text file with name - . The name is dash sign. To open this file we will use ./-name
> cat ./-

The password we got: 


Level 3
-------------
STATEMENT

The password for the next level is stored in a file called **spaces in this filename** (this is the exact name) located in the home directory

Commands you may need to solve this level
ls, cd, cat, file, du, find

SOLVE

> ssh bandit2@bandit.labs.overthewire.org -p 2220
> cat spaces\ in\ this\ filename

The password we got: 


Level 4
-------------
STATEMENT

The password for the next level is stored in a hidden file in the inhere directory.

Commands you may need to solve this level
ls, cd, cat, file, du, find

SOLVE

> ssh bandit3@bandit.labs.overthewire.org -p 2220
> cd inhere
> ls -lha
> cat .hidden

The password we got: 

Level 5
-------------
STATEMENT

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

Commands you may need to solve this level
ls, cd, cat, file, du, find

SOLVE

> ssh bandit4@bandit.labs.overthewire.org -p 2220
> cd inhere
> ls -lha
> file ./*
This command show that only -file07 has ASCII text, so this is the file that contains the password.
> cat ./-file07

The password we got: 


Level 6
-------------
STATEMENT

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable

Commands you may need to solve this level
ls, cd, cat, file, du, find


SOLVE

> ssh bandit5@bandit.labs.overthewire.org -p 2220
> find * maybeinhere* -size 1033c ! -executable

The password we got: 


Level 7
-------------
STATEMENT

The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7
owned by group bandit6
33 bytes in size

Commands you may need to solve this level
ls, cd, cat, file, du, find, grep

SOLVE

> ssh bandit6@bandit.labs.overthewire.org -p 2220
> find / -user bandit7 -group bandit6 -size 33c
> cat /var/lib/dpkg/info/bandit7.password

The password we got: 



Level 8
-------------
STATEMENT

The password for the next level is stored in the file data.txt next to the word millionth

SOLVE

> ssh bandit7@bandit.labs.overthewire.org -p 2220
> cat data.txt | grep millionth

The password we got: 


Level 9
-------------
STATEMENT

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

SOLVE

> ssh bandit8@bandit.labs.overthewire.org -p 2220
> cat data.txt | sort | uniq -u

The password we got: 


Level 10
-------------
STATEMENT

The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several ‘=’ characters.

SOLVE

> ssh bandit9@bandit.labs.overthewire.org -p 2220
> strings data.txt

The password we got: 


Level 11
-------------
STATEMENT

The password for the next level is stored in the file data.txt, which contains base64 encoded data.

SOLVE

> ssh bandit10@bandit.labs.overthewire.org -p 2220
> base64 -d <<< encoded_string_with_base64

The password we got: 


Level 12
-------------
STATEMENT


SOLVE

The password we got: 


Level x
-------------
STATEMENT

SOLVE

The password we got: 


