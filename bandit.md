# Nice to have commands
`cd $(mktemp -d)`

# Level 0
I used `cat readme` to get the contents of the file which contained the password. It was `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`.

This level is trying to get us to get familiar with Unix and using its commands.

# Level 1
This level added some complexity, requiring me to type `cat ./-` to tell `cat` that `-` is the name of a file and not a flag. The password contained within was `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`.

It wants us to understand a bit more about the Unix filesystem and that `-` is a special character.

# Level 2
To handle the file with spaces in the name, I wrapped the filename in quotes and ran `cat ./"spaces in this filename"`. It contained the string `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`.

This level is teaching us that spaces always delineate arguments in a command, which can cause problems if a file we want to reference has spaces in its name. It also teaches us how to deal with it.

# Level 3
I used `cd inhere` to enter the directory that the password was stored and then `ls -a` to find the hidden password file. From there I ran `cat ...Hiding-From-You` and got `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`.

We are practicing with changing directories and dealing with hidden files.

# Level 4
After `cd inhere`, I ran `file ~/inhere/-file0[0-9]` to check the filetype of all of the files within the `inhere` directory. It told me that only `-file07` was ASCII text, so I ran `cat ./-file07` and got `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`.

This level is teaching us about filetypes and that not all files are human-readable ASCII format. It is also giving us more practice dealing with annoying filenames.

# Level 5
Using the `find` command, I ran `find -size 1033c ! -executable -print` which looks for a file that is 1033 bytes (`-size 1033c`) and is not an executable (`! -executable`) and print the matching results to stdout (`-print`). It thankfully only gave one option, `./maybehere07/.file2`, so I ran `cat ./maybehere07/.file2` and got the password `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`.

This level would have been really tedious without the `find` command, so it kind of forces you to learn how to use it effectively. At the same time, it teaches you about the types of files and that some files can be executables.

# Level 6
Since we have to search the entire server, before running `find`, I used `cd /` to change directory to the root directory. I then ran `find -user bandit7 -group bandit6 -size 33c -print` which looks for a file that is owned by user `bandit7` (`-user bandit7`), owned by group `bandit6` (`-group bandit6`) and is 33 bytes large (`-size 33c`). This gave me a lot of "Permission denied" errors, but also gave me the path `./var/lib/dpkg/info/bandit7.password`. Running `cat ./var/lib/dpkg/info/bandit7.password` then gave me `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`.

We are learning about user and group permissions, and how even though we are logged in as `bandit6` we can still access a file owned by `bandit7` because we are in a group that has permission to read it.


# Level 7
To find the password that is on the same line as "millionth", I ran `cat data.txt | grep millionth` which pipes the contents of `data.txt` into the `grep millionth` command which returns any lines that have the word "millionth" on it. This gave me `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`.

This is helping us learn how to use `grep`.

# Level 8
I first tried to use `uniq -u data.txt` to find the one unique line, but after reading the `man` pages for `uniq`, I realized that the lines had to be sorted for `uniq` to find unique lines. Therefore, I ran `sort data.txt | uniq -u` and got `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`.

It is helping us learn how to use `uniq`. 

# Level 9
I used `strings data.txt` to find the strings in `data.txt` and then combed through the output until I found the password `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`.

We are learning how to use `strings`.

# Level 10
I ran `base64 -d data.txt` and got the password `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`.

It is teaching us how to use `base64`.

# Level 11
I ran the command `cat ./data.txt | tr nopqrstuvwxyzabcdefghijklmNOPQRSTUVWXYZABCDEFGHIJKLM abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ` to unshift each letter and got `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`

We are learning how to use `tr` to deal with data that has been obfuscated by the Caesar cipher.

# Level 12
`mktemp -d`
`cd /tmp/tmp.OIXyRfJPHw`
`cp ~/data.txt .`
`xxd -r data.txt | gunzip | bunzip2 | gunzip | tar -x`
`tar -xf ./data5.bin`
`tar -xf ./data6.bin`
`gunzip -c data8.bin`
`FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

We are practicing (a TON) with (de)compression tools.

# Level 13
`ssh -i ~/sshkey.private ssh://bandit14@bandit.labs.overthewire.org:2220`
`cat /etc/bandit_pass/bandit14`
`MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS`

Practicing ssh-ing, and specifically ssh-ing with a private key to access a remote file.

# Level 14
`telnet bandit.labs.overthewire.org 30000`
`MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS`
`8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`

Learning how to submit data to a remote server on a specific port.

# Level 15
`openssl s_client -connect bandit.labs.overthewire.org:30001`
`8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`
`kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx`

Practicing how to connect and send data over an SSL connection.

# Level 16
`nmap bandit.labs.overthewire.org -p 31000-32000`
`openssl s_client -connect -quiet bandit.labs.overthewire.org:31790`

```
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```

# Level 17
`cd $(mktemp -d)`
`vi sshkey.private`
(put the RSA private key in `sshkey.private`)
`chmod 700 sshkey.private`
`ssh -i ./sshkey.private ssh://bandit17@bandit.labs.overthewire.org:2220`

# Level 18
`diff passwords.new passwords.old`
`cat passwords.new | grep x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO` (make sure which one is in `passwords.new`)
`x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO`
