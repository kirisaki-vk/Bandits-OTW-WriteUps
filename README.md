---
title: Write up of Over The Wire's Bandit game
---

# Write up of Over The Wire's Bandit game

- ## **Information**
    This repo contains my solutions to the game **bandit** found on the [OverTheWire](https://overthewire.org/) website.

    Solutions are down bellow.

- ## **Solutions**

    On the begin I'd like to mention that in this game we will ssh to `bandit.labs.overthewire.org` most of the time so it will be our **host server**.

    - ### **Level 0**
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
        - You will need to login to ssh as `bandit1` on the host server on the usual port `2220` by the following command:
        ```bash
        $ ssh bandit1@bandit.labs.overthewire.org -p 2220
        ```
        > The passe
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
        - To solve this level you will need to first login into the host server as `bandit2` on the usual port `2220`. Here is the command for it:
        ```bash
        $ ssh bandit2@bandit.labs.overthewire.org -p 2220
        ```
        > The passmord of the user `bandit2` is the one we've found in Level 1.

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
        - You will need to ssh into the host server as the user `bandit3` on the usual port `2220`. Which gives the following command:

        ```bash
        $ ssh bandit3@bandit.labs.overthewire.org -p 2220
        ```
        > The password for the user `bandit3` is the one we've found on Level 2

        - Then by executing `ls` you will find only one directory called `inhere`
        - Change to that directory by using the command `cd`
        ```bash
        $ cd inhere
        ```
        - Then by executing `ls -a` you will find one file hidden named `.hidden`
        - To show it's content we will use `cat`
        ```bash
        $ cat .hidden
        ```
        Executing it will give you as output:

        ```
        2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
        ```
        That's the password to pass to the next level. You can now logout and pass to the next level.

    - ## **Level 4**
        - First, you will need to ssh into the host server on the usual port:

        ```bash
        $ ssh bandit4@bandit.labs.overthewire.org -p 2220
        ```
        > The password for the user `bandit4` is the one we've found on Level 3

        - Then you 
        