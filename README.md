# overthewire. Bandit

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

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

SOLVE

> ssh bandit11@bandit.labs.overthewire.org -p 2220

> cat data.txt | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'

The password we got: 

Level 13
-------------
STATEMENT

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

SOLVE

> ssh bandit12@bandit.labs.overthewire.org -p 2220

> mkdir /tmp/alex

> cp data.txt /tmp/alex

> xxd -r data.txt >> reverse_archive

> zcat reverse > data

> bzip2 -d data

> zcat data.out > data2

> tar -xvf data2

> tar -xvf data5.bin

> bzip2 -d data6.bin

> zcat data8.bin > final

> cat final

The password we got: 


Level 14
-------------
STATEMENT

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

SOLVE

> ssh bandit13@bandit.labs.overthewire.org -p 2220

> ssh bandit14@localhost -i sshkey.private

> cat /etc/bandit_pass/bandit14

The password we got: 


Level 15
-------------
STATEMENT

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

SOLVE

> nc localhost 300000

The password we got: 


Level 16
-------------
STATEMENT

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

SOLVE

> openssl s_client -connect localhost: 30001

The password we got: 

Level 17
-------------
STATEMENT

The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

SOLVE

> nmap -sT -A -p 31000-32000

We found out that only port 31790 is open.

> openssl s_client -connect localhost: 31790


Level 18
-------------
STATEMENT

There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

SOLVE

> cd ~

> nano sshkey.private

Paste the pivate key from the last level.

> diff pasword.old password.new

The password we got: 


Level 19
-------------
STATEMENT

The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

SOLVE

> ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme

The password we got: 


Level 20
-------------
STATEMENT

To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

SOLVE

> ssh bandit19@bandit.labs.overthewire.org -p 2220

> ./bandit20-do id

> ./bandit20-do whoami

> ./bandit20-do cat /etc/bandit_pass/bandit20

The password we got: 


Level 21
-------------
STATEMENT

There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think

SOLVE

For this challenge we need to use 2 terminals, both connected via ssh to bandit20. We need to send the password of the last level and get back a new password.

both:
> ssh bandit20@bandit.labs.overthewire.org -p 2220

first:
> nmap localhost

> echo "last_level_password" | nc -l -p 60000

Next a password will appear.

second:

> ./suconnect 60000


The password we got: 


Level 22
-------------
STATEMENT

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

Commands you may need to solve this level
cron, crontab, crontab(5) (use “man 5 crontab” to access this)

SOLVE

> ssh bandit21@bandit.labs.overthewire.org -p 2220

> cd /etc/cron.d

> cat /usr/bin/cronjob_bandit22.sh

> cat /tmp/t706...

The password we got: 


Level 23
-------------
STATEMENT

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

SOLVE

> ssh bandit22@bandit.labs.overthewire.org -p 2220

> cd /etc/cron.d

> cat cronjob_bandit23

> cat /usr/bin/cronjob_bandit23.sh

> echo I am user bandit23 | md5sum | cut -d ' ' -f 1

> cat /tmp/8ca3...

The password we got: 



Level 24
-------------
STATEMENT

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

SOLVE

> ssh bandit23@bandit.labs.overthewire.org -p 2220

> cd /etc/cron.d

> cat cronjob_bandit23

> cat /usr/bin/cronjob_bandit24.sh

Make a directory in /tmp folder and create a bash script:

#!/bin/bash 
cat /etc/bandit_pass/bandit24 >> /tmp/numeDirector/nextPassword

> cp script.sh /var/spool/bandit24

Check the created folder,numeDirector, for the nextPassword file.


The password we got: 


Level 25
-------------
STATEMENT

A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.

SOLVE

We need to create a bash script that will check every 4-digit code. The script is located in the folder created for the last level.

#!/bin/bash

for i in{0000..9999}
  echo "password $i" | nc localhost 30002

The password we got: 

Level 26
-------------
STATEMENT

Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

SOLVE

The momment we login, we are logout. This level was tricky, i admit i searched the answer on the internet and without this i could not pass this level. Before login we need to minimize the terminal window so we can enter more. To enter vim we need to press v. 

> ssh -i bandit26.sshkey bandit26@localhost

:set shell=/bin/bash
:shell

After this we are bandit26.

The password we got: 


Level 27
-------------
STATEMENT

Good job getting a shell! Now hurry and grab the password for bandit27!

SOLVE

After we execute ls, we see that we have a suid file and a text file. The text file doesn't have the password as we expect, so we need to use the suid file

> ./bandit26 id

> ./bandit26 whoami

> ./bandit26 cat /etc/bandit_pass/bandit27

The password we got: 

Level 28
-------------
STATEMENT

There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo. The password for the user bandit27-git is the same as for the user bandit27.

Clone the repository and find the password for the next level.

SOLVE

> ssh bandit27@bandit.labs.overthewire.org -p 2220

> git clone  ssh://bandit27-git@localhost/home/bandit27-git/repo destinationFolder

> cat README

The password we got: 


Level 29
-------------
STATEMENT

There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo. The password for the user bandit28-git is the same as for the user bandit28.

Clone the repository and find the password for the next level.

SOLVE

> ssh bandit29@bandit.labs.overthewire.org -p 2220

> git clone ssh://bandit27-git@localhost/home/bandit28-git/repo destinationFolder

> git log

> git log -p -1

The password we got: 



Level 30
-------------
STATEMENT

There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo. The password for the user bandit30-git is the same as for the user bandit30.

Clone the repository and find the password for the next level.

SOLVE


The password we got: 



Level x
-------------
STATEMENT

SOLVE

The password we got: 


