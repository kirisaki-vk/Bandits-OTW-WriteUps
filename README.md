# Write up of Over The Wire's Bandit game

- ## **Information**
    This repo contains my solutions to the game **bandit** found on the [OverTheWire](https://overthewire.org/) website.

    Solutions are down bellow.

- ## **Solutions**

    On the begin I'd like to mention that in this game we will ssh to `bandit.labs.overthewire.org` most of the time so it will be our **host server**.

    - ### **Level 0**
        1. ### **Hint** 
        The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in,

        2. ### **Solution**
        - On first you will need to ssh into the game server which is hosted in `bandit.labs.overthewire.org` on the port `2220` as the user `bandit0`.
        That is done by the following command:
        ```bash
        $ ssh bandit0@bandit.labs.overthewire.org -p 2220

        ```
        > NB: The password of `bandit0` is `bandit0`

         - By executing the command `ls` you will find that there is one file called `readme` which contains the actual password to login into user `bandit1`. To see it's content, just execute the command:
        ```bash
        $ cat readme
        ```
        That last command will give you the password of the user `bandit2`.It should give the following output:

        ```
        NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
        ```

        That's the key to pass into the next Level. Type now `logout` and press Enter to logout.

    - ## **Level 1**
        1. ### **Hint** 
        The password for the next level is stored in a file called `-` located in the home directory.

        2. ### **Solution**
        - You will need to login to ssh as `bandit1` on the host server on the usual port `2220` by the following command:
        
        ```bash
        $ ssh bandit1@bandit.labs.overthewire.org -p 2220
        ```
        
        > The password for the user `bandit1` is the one discovered on the [Level 0](#level-0)

        - Now executing the command `ls` you will find only one file named `-`
        - To see it's content, you will need to execute this command:

        ```bash
        $ cat ./-
        ```

        Which will output:

        ```
        rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
        ```

        That is the password to the `bandit2`. Now you can logout.


    - ## **Level 2**
        1. ### **Hint** 
        The password for the next level is stored in a file called `spaces in this filename` located in the home directory

        2. ### **Solution**
        - To solve this level you will need to first login into the host server as `bandit2` on the usual port `2220`. Here is the command for it:

        ```bash
        $ ssh bandit2@bandit.labs.overthewire.org -p 2220
        ```

        > The password of the user `bandit2` is the one we've found in Level 1.

        - By executing the command `ls` you will find a file named `spaces in this filename`

        - To see the content of the file, you will need to replace spaces by `\ ` which will tell the command to consider the space as a part of the filename. So this will be the commad to open it:

        ```bash
        $ cat spaces\ in\ this\ filename
        ```

        Executing it will give you as output:

        ```
        aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
        ```

        That's the password to pass to the next level. You can now logout and pass to the next level.

    - ## **Level 3**
        1. ### **Hint** 
        The password for the next level is stored in a hidden file in the `inhere` directory.

        2. ### **Solution**
        - You will need to ssh into the host server as the user `bandit3` on the usual port `2220`. Which gives the following command:

        ```bash
        $ ssh bandit3@bandit.labs.overthewire.org -p 2220
        ```

        > The password for the user `bandit3` is the one we've found on Level 2

        - Then by executing `ls` you will find only one directory called `inhere`
        - Change to that directory by using the command `cd`:

        ```bash
        $ cd inhere
        ```

        - Then by executing `ls -a` you will find one file hidden named `.hidden`

        - To show it's content we will use `cat`:

        ```bash
        $ cat .hidden
        ```

        Executing it will give you as output:

        ```
        2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
        ```

        That's the password to pass to the next level. You can now logout and pass to the next level.

    - ## **Level 4**
        1. ### **Hint** 
        The password for the next level is stored in the only **human-readable** file in the `inhere` directory. **Tip**: if your terminal is messed up, try the “reset” command.

        2. ### **Solution**
            - First, you will need to ssh into the host server on the usual port:

            ```bash
            $ ssh bandit4@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit4` is the one we've found on [Level 3](#level-3)

            - Then by listing all the content of the home directory by using `ls` you will find a folder named `inhere`

            - We will use `cd` to change the `inhere` directory. we will use the command:
            
            ```bash
            $ cd `inhere`
            ```

            - Then we will find all human-readable format files by using the command `file` and by taking it's result and filtering only files encoded with `ascii`. That's done by executing the command:

            ```bash
            $ file -i ./* | grep -i ascii
            ```

            - You should get as output:

            ```bash
            ./-file07: text/plain; charset=us-ascii
            ```

            It tells us that the only human-readable format file is the file named `-file07`, so this contains the password to the Level 5,
            opening it with `cat` gives us the output:

            ```bash
            $ cat ./-file07
            lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
            ```

            That's the password to pass to the next level. You can now logout and pass to the next level.

    - ## **Level 5**
        1. ### **Hint** 
        The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

        - human-readable
        - 1033 bytes in size
        - not executable

        2. ### **Solution**
            - First, you will need to ssh into the host server on the usual port as the user `bandit5`:

            ```bash
            $ ssh bandit5@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit5` is the one we've found on [Level 4](#level-4)

            - Then you will need to find the file matching all the conditions in the hint by using the command `find` and showing it's content by using `cat` wich is done by executing this command:

            ```bash
            $ cat $(find . -maxdepth 3 -size 1033c ! -executable)
            ```

            This command will output the password for the user `bandit6` which is on the next Level

            ```
            P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
            ```

    - ## **Level 6**
        1. ### **Hint** 
        The password for the next level is stored somewhere on the server and has all of the following properties:

        - owned by user bandit7
        - owned by group bandit6
        - 33 bytes in size

        2. ### **Solution**
            - First, ssh into the host server as the user `bandit6`

            ```bash
            $ ssh bandit6@bandit.labs.overthewire.org -p 2220
            ```
            > The password for the user `bandit6` is the same as the password we've found on the [Level 5](#level-5)

            - Then we will use the command `find` to search for the file

            ```bash
            $ find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
            ```

            - It will output the file which match all the conditions in the hint

            ```
            /var/lib/dpkg/info/bandit7.password
            ```

            - We can see it's content by using the command `cat`

            ```bash
            $ cat /var/lib/dpkg/info/bandit7.password
            ```

            That will return the password for the next Level.

            ```
            z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
            ```


    - ## **Level 7**
        1. ### **Hint** 
        The password for the next level is stored in the file `data.txt` next to the word `millionth`

        2. ### **Solution**
            - First ssh into the host server as the user `bandit7`

            ```bash
            $ ssh bandit7@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit7` is the one we've found on the [Level 6](#level-6)

            - Then we will just need to output the line into the file data.txt which contains the world `millionth` by using the command `cat` and `grep`

            ```bash
            $ cat data.txt | grep -i millonth
            ```

            - You should have the following output

            ```
            millionth TESKZC0XvTetK0S9xNwm25STk5iWrBvP
            ```

            So the password for the next Level is `TESKZC0XvTetK0S9xNwm25STk5iWrBvP` 

    - ## **Level 8**
        1. ### **Hint** 
        The password for the next level is stored in the file `data.txt` and is the only line of text that occurs only once

        2. ### **Solution**
            - First ssh into the host server as the user `bandit8`

            ```bash
            $ ssh bandit8@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit8` is the one we've found on the [Level 7](#level-7)

            - Then to find the unique line into the file data.txt, we will use `cat`, `sort` and `uniq`

            ```bash
            $ cat data.txt | sort | uniq -u
            ```

            It will give the following output:

            ```
            EN632PlfYiZbn3PhVK3XOGSlNInNE00t
            ```

            That is the password to the next Level

    - ## **Level 9**
        1. ### **Hint** 
        The password for the next level is stored in the file `data.txt` in one of the few human-readable strings, preceded by several `=` characters.

        2. ### **Solution**
            - First ssh into the host server as the user `bandit9`

            ```bash
            $ ssh bandit9@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit9` is the one we've found on the [Level 8](#level-8)

            - Then to see all the strings that contains several `=` spaces into the file `data.txt` we will use the command `strings` and `grep`

            ```bash
            $ strings data.txt | grep ^======
            ```

            You should get the following output which is the password for the next Level
            
            ```
            ========== password
            ========== is
            ========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
            ```

    - ## **Level 10**
        1. ### **Hint** 
        The password for the next level is stored in the file `data.txt`, which contains base64 encoded data

        2. ### **Solution**
            - First ssh into the host server as the user `bandit10`

            ```bash
            $ ssh bandit10@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit10` is the one we've found on the [Level 9](#level-9)

            - To decode the base64 encoded password, we will use the command `base64`

            ```bash
            $ base64 --decode data.txt
            ```

            It will give you as output the password to the next Level

            ```
            The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
            ```

    - ## **Level 11**
        1. ### **Hint** 
        The password for the next level is stored in the file `data.txt`, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

        2. ### **Solution**
            - First ssh into the host server as the user `bandit11`

            ```bash
            $ ssh bandit11@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit11` is the one we've found on the [Level 10](#level-10)

            - Then to decode the password ciphered with [Rot 13](https://en.wikipedia.org/wiki/ROT13) we will use the command `tr`

            ```bash
            $ tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt
            ```

            It should output password to the next Level

            ```
            The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
            ```

    - ## **Level 12**
        1. ### **Hint** 
        The password for the next level is stored in the file `data.txt`, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

        2. ### **Solution**
            - First ssh into the host server as the user `bandit12`

            ```bash
            $ ssh bandit12@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit12` is the one we've found on the [Level 11](#level-11)

            - We will need to create a temp directory to work on by using the command `mktmp` and go into it by using cd

            ```bash
            $ cd $(mktemp -d)
            ```


            - Then to convert the hexdump to the original comressed file by using `xxd`

            ```bash
            $ xxd -r ~/data.txt data.gz
            ```

            - Now we will perform some decompressions to reach the final file which contains the password by using `tar`, `bzip2` and `gunzip`

            ```bash
            $ gunzip data.gz && mv data data.bz2 && bzip2 -d data.bz2 && mv data data.gz && gunzip data.gz && tar -xf data && tar -xf data5.bin && bzip2 -d data6.bin && tar -xf data6.bin.out && mv data8.bin data8.gz && gunzip data8.gz && cat data8 2>/dev/null

            ```

            You should have the following output

            ```
            bzip2: Can't guess original name for data6.bin -- using data6.bin.out
            The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
            ```

            You now have the password to the next Level.

    - ## **Level 13**
        1. ### **Hint** 
        The password for the next level is stored in `/etc/bandit_pass/bandit14` and **can only be read by user bandit14**. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. **Note**: localhost is a hostname that refers to the machine you are working on

        2. ### **Solution**
            - First ssh into the host server as the user `bandit13`

            ```bash
            $ ssh bandit13@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit13` is the one we've found on the [Level 12](#level-12)

            - Now to add the credentials in the home directory, we will first need to start the ssh agent by using the command `eval` and `ssh-agent`

            ```bash
            $ eval $(ssh-agent)
            ```

            - Then you will need to add the RSA key to ssh by using `ssh-add`

            ```bash
            $ ssh-add sshkey.private
            ```

            - After that you will need to ssh into the `localhost` as the user `bandit14`

            ```bash
            $ ssh bandit14@localhost -p 2220
            ```

            - Finaly you will need to see the content of the file `/etc/bandit_pass/bandit14` by using the command `cat`

            ```bash
            $ cat /etc/bandit_pass/bandit14
            ```

            That should give you the following output

            ```
            fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
            ```

            That's the password to the next Level

    - ## **Level 14**
        1. ### **Hint**
        The password for the next level can be retrieved by **submitting the password of the current level to port 30000 on localhost.**

        2. ### **Solution**
            - First ssh into the host server as the user `bandit14`

            ```bash
            $ ssh bandit14@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit14` is the one we've found on the [Level 13](#level-13)

            - To submit the password of the current Level through the port `30000` by using the command `nc`

            ```bash
            $ nc localhost 30000
            ```

            - Now that we're are connected to the port `30000`, we can submit the password by just pasting in and press Enter

            It should give you:

            ```bash
            $ nc localhost 30000
            fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
            Correct!
            jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
            ```

            Now you've got the password to the next Level

            > To logout, you need first exit to the nc command by pressing `Ctrl+C` and then you can execute `logout`

    - ## **Level 15**
        1. ### **Hint** 
        The password for the next level can be retrieved by **submitting the password of the current level to port 30001 on localhost using SSL encryption.**

        2. ### **Solution**
            - First ssh into the host server as the user `bandit15`

            ```bash
            $ ssh bandit15@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit15` is the one we've found on the [Level 14](#level-14)

            - Now we can connect to the SSL by using `openssl` command

            ```bash
            $ openssl s_client -connect localhost:30001
            ```

            - If you see now `read R BLOCK` that mean that you're connected successfully. Now you can submit the password by just pasting it there and then press Enter.

            - That should give you the password to the next Level

            ```
            jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
            Correct!
            JQttfApK4SeyHwDlI9SXGR50qclOAil1

            closed
            ```

            You can now logout and pass to the next Level

    - ## **Level 16** 
        1. ### **Hint** 
        The credentials for the next level can be retrieved by submitting the password of the current level to **a port on localhost in the range 31000 to 32000**. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

        2. ### **Solution**
            - First ssh into the host server as the user `bandit16`

            ```bash
            $ ssh bandit16@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit16` is the one we've found on the [Level 15](#level-15)

            - To scan all available server into those given range of ports, we can use the command `nmap`

            ```bash
            $ nmap -sV localhost -p 31000-32000
            Starting Nmap 7.80 ( https://nmap.org ) at 2023-05-07 10:55 UTC
            Nmap scan report for localhost (127.0.0.1)
            Host is up (0.00016s latency).
            Not shown: 996 closed ports
            PORT      STATE SERVICE     VERSION
            31046/tcp open  echo
            31518/tcp open  ssl/echo
            31691/tcp open  echo
            31790/tcp open  ssl/unknown
            31960/tcp open  echo
            ```

            - By running it, we can see that there is 2 ports with SSL with one runing `echo` so we can try the one wich runs an `unknown` service. To connect on it, we will use the command `openssl`

            ```bash
            $ openssl s_client -connect localhost:31790
            ```

            - We can now submit the password of the current Level as we did on the previous Level and should get as output

            ```
            JQttfApK4SeyHwDlI9SXGR50qclOAil1
            Correct!
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

            closed
            ```

            Instead of obtaining the password to the next Level, we've obtained an SSH private key to connect as the user `bandit17`

            > We must save it localy **on our own device** as a plain text file

            > - Note: To add an ssh key, you should first start the ssh agen with the command `eval $(ssh-agent)` then add the ssh key with the command `ssh-add <path-to-the-key>`. As we've seen on [Level 13](#level-13)

    - ## **Level 17**
        1. ### **Hint** 
        There are 2 files in the homedirectory: **passwords.old and passwords.new**. The password for the next level is in passwords.new and is **the only line that has been changed between passwords.old and passwords.new**

        2. ### **Solution**
            - To login, you will need first add the private ssh key on our local PC
            then we can connect as the user `bandit17`

            - We can use the command `diff` to see the difference between the old and new password

            ```bash
            $ diff passwords.old passwords.new
            ```

            - You should have the following output:

            ```
            42c42
            < glZreTEH1V3cGKL6g4conYqZqaEj0mte
            ---
            > hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
            ```
            
            - So the password is the second one which is the changed to the old line which is `hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg`

            You can now pass to the next Level

    - ## **Level 18**
        1. ### **Hint** 
        The password for the next level is stored in a file `readme` in the homedirectory. Unfortunately, someone has modified `.bashrc` to log you out when you log in with SSH.

        2. ### **Solution**
            You will not be able to login as the user `bandit18` because the .bashrc file will log you out when you login, but we know that the password to the next Level is into the file called `readme` on `bandit18`'s home we can execute a command by passing it after all the ssh commmand parameter. The command would be:

            ```bash
            ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
            ```
            That should output at the end of the line the password for the next Level and then log you out.

            ```
            VxCazJaVykI6W36BkBU0mJTCM8rR95XT
            ```

    - ## **Level 19**
        1. ### **Hint** 
        To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place `/etc/bandit_pass`, after you have used the setuid binary.

        2. ### **Solution**
            - First ssh into the host server as the user `bandit19`

            ```bash
            $ ssh bandit19@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit19` is the one we've found on the [Level 18](#level-18)

            - We can use the binary `bandit20-do` to execute a comand as if we are the user `bandit20`, so to pass it, we can see the content of the file in `/etc/bandit_pass/bandit20` wich contains the password for the next Level and owned by the user `bandit20` by the following command:

            ```bash
            $ ./bandit20-do cat /etc/bandit_pass/bandit20
            ```

            That should give you as output:

            ```
            VxCazJaVykI6W36BkBU0mJTCM8rR95XT
            ```

            So that's the password to the next Level

    - ## **Level 20**
        1. ### **Hint** 
        There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

        2. ### **Solution**
            - First ssh into the host server as the user `bandit20`

            ```bash
            $ ssh bandit20@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit20` is the one we've found on the [Level 19](#level-19)

            - For this level we will use the commant `nc` to send the actual password through the an a port that we will choose, I've choosed the port `31542` and will send it to the background with `&`:

            ```bash
            $ echo VxCazJaVykI6W36BkBU0mJTCM8rR95XT | nc -l localhost 31542 &
            ```

            - Now I can launch the binary `suconnect` which will take the message from the port I've choosed with the command:

            ```bash
            $ ./suconnect 31542
            ```

            It should give the following output:

            ```
            Read: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
            Password matches, sending next password
            NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
            ```

            You can now pass to the next Level
    
    - ## **Level 21**
        1. ### **Hint** 
        A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in `/etc/cron.d/` for the configuration and see what command is being executed.

        2. ### **Solution**
            - First ssh into the host server as the user `bandit21`

            ```bash
            $ ssh bandit21@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit21` is the one we've found on the [Level 20](#level-20)

            - We need to see the cronjob script for the next user which is `bandit22` 

            ```bash
            $ cat /etc/cron.d/cronjob_bandit22
            @reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
            * * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
            ```

            - That tells us that the scheduled tasks run by `cron` for this user is located at `/usr/bin/cronjob_bandit22.sh`. We can now show it's content:

            ```bash
            $ cat /usr/bin/cronjob_bandit22.sh
            #!/bin/bash
            chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
            cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
            ```

            So we should look at the file `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv` which contains the password for the next Level

            ```bash
            $ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
            WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff
            ```

            We can now pass to the next Level

    - ## **Level 22**
        1. ### **Hint** 
        A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in `/etc/cron.d/` for the configuration and see what command is being executed.

        2. ### **Solution**
            - First ssh into the host server as the user `bandit22`

            ```bash
            $ ssh bandit22@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit22` is the one we've found on the [Level 21](#level-21)

            - We can see the cronjob for this user in the usual directory:

            ```bash
            $ cat /etc/cron.d/cronjob_bandit23
            @reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
            * * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
            ```

            - So we should do:

            ```bash
            $ cat /usr/bin/cronjob_bandit23.sh
            #!/bin/bash

            myname=$(whoami)
            mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

            echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

            cat /etc/bandit_pass/$myname > /tmp/$mytarget
            ```

            - This output tells us that the file containing the password to the next level is into the variable `$mytarget` which is the result of the command `echo I am user $myname | md5sum | cut -d ' ' -f 1`. This command will be run as the user `bandit23` so `$myname` is `bandit23`. So we can know the name of the file containing the password to the next level by executing the command above but replacing `$myname` to `bandit23`:

            ```bash
            $ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
            8ca319486bfbbc3663ea0fbe81326349
            ```

            - So the name of the file we're searching for is `8ca319486bfbbc3663ea0fbe81326349` and is located in the directory `/tmp/`

            ```bash
            $ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
            QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
            ```

            So you can now pass to the next level

    - ## **Level 23**
        1. ### **Hint** 
        A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in `/etc/cron.d/` for the configuration and see what command is being executed.

        2. ### **Solution**
            - First ssh into the host server as the user `bandit23`

            ```bash
            $ ssh bandit23@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit23` is the one we've found on the [Level 22](#level-22)

            - We will need first see the cronjob for the user `bandit24`

            ```bash
            $ cat /etc/cron.d/cronjob_bandit24
            @reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
            * * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
            ```

            - As we've seen from previous Levels, we should then see what's inside the file `/usr/bin/cronjob_bandit24.sh`

            ```bash
            $ cat /usr/bin/cronjob_bandit24.sh
            #!/bin/bash

            myname=$(whoami)

            cd /var/spool/$myname/foo || exit 1
            echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
            for i in * .*;
            do
                if [ "$i" != "." -a "$i" != ".." ];
                then
                    echo "Handling $i"
                    owner="$(stat --format "%U" ./$i)"
                    if [ "${owner}" = "bandit23" ]; then
                        timeout -s 9 60 ./$i
                    fi
                    rm -rf ./$i
                fi
            done

            ```

            - This scripts then will execute any script owned by the user `bandit23` with the rights of the user `bandit24` located in the directory `/var/spool/bandit24/foo`

            > So to pass this we can write a script that will copy the password into a file that we will see the content after

            - First let's create our temporary working directory and go into it

            ```bash
            $ cd $(mktemp -d)
            ```

            - Now let's create the script that will be executed

            ```bash
            $ nano cppassword.sh
            ```

            > You can paste into it the following script wich will do the copy of the password.

            ```bash
            #!/bin/bash

            pswd_dir=/tmp/bandit24password
            mkdir $pswd_dir
            chmod 777 $pswd_dir
            touch $pswd_dir/bandit24
            cat /etc/bandit_pass/bandit24 > $pswd_dir/bandit24

            ```

            > To save and quit on nano, just press `CTRL+X` and then `Y`

            - Now we should edit the permissions of the permissions of our script to be executable with `chmod`

            ```bash
            $ chmod +rwx cppassword.sh
            ```

            - Then copy it to the directory where the script of the cronjob will execute it

            ```bash
            $ cp cppassword.sh /var/spool/bandit24/foo
            ```

            - Then after few seconds (~10 seconds) the script of the cronjob will execute it and we can now see the password of the next Level where the our script saved it

            ```bash
            $ cat /tmp/bandit24password/bandit24
            VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
            ```

            So we can no go to the next level

    - ## **Level 24**
        1. ### **Hint** 
        A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing. You do not need to create new connections each time

        2. ### **Solution**
            - First ssh into the host server as the user `bandit24`

            ```bash
            $ ssh bandit24@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit24` is the one we've found on the [Level 23](#level-23)

            - To find the correct pincode to get the correct password by bruteforce, we will again use a script that will test all the combinations possible for us then output the it

            - First let's create a temporary working directory

            ```bash
            $ cd $(mktemp -d)
            ```
            
            - Now let's create the script

            ```bash
            $ nano brute_force.sh
            ```

            - Then paste into it :

            ```bash
            #!/bin/bash

            for i in {0000..9999};
            do  
                echo VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar $i >> codes 
            done

            cat codes | nc localhost 30002 > log.txt
            cat log.txt | grep -v Wrong

            ```

            - Quit and save it, now we can execute it:

            ```bash
            $ sh brute_force.sh
            ```

            - After a moment it will quit and give you the following output:

            ```bash
            I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
            Correct!
            The password of user bandit25 is p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d

            Exiting.
            ```

            So now we can pass the next level

    - ## **Level 25**
        1. ### **Hint** 
        Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not `/bin/bash`, but something else. Find out what it is, how it works and how to break out of it.

        2. ### **Solution**
            - First ssh into the host server as the user `bandit25`

            ```bash
            $ ssh bandit25@bandit.labs.overthewire.org -p 2220
            ```

            > The password for the user `bandit25` is the one we've found on the [Level 24](#level-24)

            - By doing the command `ls`, we will find one file called `bandit26.sshkey` which is a private ssh key. We will need to save this ssh key to our locale machine and add it so we can ssh into the user `bandit26`

            > We've already seen how to add an ssh-key no [ older levels](#level-13)

            - Then we need to check what shell the user bandit26 used. We do this by looking in the correct line in the ‘passwd’ file.

            ```bash
            
            $ cat /etc/passwd | grep bandit26
            bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
            
            $ ls -la /usr/bin/showtext
            -rwxr-xr-x 1 root root 53 May  7  2020 /usr/bin/showtext
            
            $ cat /usr/bin/showtext
            #!/bin/sh

            export TERM=linux

            more ~/text.txt
            exit 0
            ```

            - So we have the connection closed after login in because on login, we do not execute the shell but a program called `more` which opens a file called `text.txt` on the home directory.

            > `more` command is used to view the text files in the command prompt, displaying one screen at a time in case the file is large (For example log files). The more command also allows the user do scroll up and down through the page.

            - Since the text shown by `more` is not large enough to make it enter in interactive mode, we will need to resize our terminal to be small enough to put it in interactive mode then enter reconnect and press `v` when `more` is in interactive mode to open `vim` which is a text editor on terminal like `nano`
            
            - When entered in vim, we can now type:

            ```
            :e /etc/bandit\_pass/bandit26
            ```

            - By pressing enter, it will open the file containing the password to the next Level

            ```
            c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1
            ```

