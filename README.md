# Bandit-CTF
OverTheWire Bandit is a linux based Capture the Flag wargame designed for beginners to dive into the world of Linux, Networking, Cybersecurity and Capture the flag wargames. This is where I will publish my walkthroughs and progress through the Bandit Capture The Flag.
All of this will be done using an Oracle Virtual Machine running Kali Linux.

# Level 0

## Level Goal
The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

## Walkthrough

We are told in the level goal we will need to log into the game server using SSH, we are also given the host server address which is bandit.labs.overthewire.org and that it is on port 2220. We are also given the username for the level which is bandit0. We can use this information to construct a command as follows.

```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
After running the command we will be prompted to enter a password to continue to the level, this password is bandit0 as stated in the level goal above.

![bandit0-terminal-commands-screenshot](https://raw.githubusercontent.com/EoinReid/Bandit-CTF/master/Bandit-Screencaps/bandit0-1.PNG "Bandit0 Terminal Commands")


## Commands breakdown

```
ssh 
```
Secure Shell (SSH) is a cryptographic network protocol for operating network services securely over an unsecured network.

```
bandit0@bandit.labs.overthewire.org
```
Bandit0 is the username we were given in the level goal descriptor and bandit.labs.overthewire.org is the server address we want to connect to so we specify we want to connect to that address with the bandit0 username using the @ symbol inbetween them.

```
-p 2220
```
The -p attribute is used to specify a port number for our command as we were given the port number 2220 in the level goal descriptor, we needed to specify this in our command.


# Level 0 → Level 1

## Level Goal
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

## Walkthrough

We are told in the level goal descriptor that the password for the next level is stored in a file called readme in the home directory. So first we need to check if we are in the home directory. We do this using the pwd command.

```
pwd
```
After the pwd command confirms we are in the home directory we need to list the contents of the directory to see whats there we do this using the ls command.

```
ls
```

From the ls command we can see there is a file called "readme" in the home directory, so we are going to use the cat command to see the contents of this file.

```
cat readme
```

From this command we have captured our flag for this level and obtained the password.

### Flag captured
```
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```
After capturing our flag we are going to move to the next level, which is called bandit1, using the following command.

```
ssh bandit1@localhost
```
Enter the flag from above when prompted for the password for the next level.

![bandit01-terminal-commands-screenshot](https://raw.githubusercontent.com/EoinReid/Bandit-CTF/master/Bandit-Screencaps/bandit01-1.PNG "Bandit01 Terminal Commands")

## New Commands breakdown

```
pwd 
```
pwd or Print Working Directory does what it says on the tin, it prints the working directory aka the directory you are currently in to the terminal to let you know where in the file system you are located.

```
ls
```
ls or List Directories is a command used to list directories and files in the current directory by default, however you can specify which path you want to list the directories of.

```
cat readme
```
cat, short for concatenate is a command that not only displays file contents but it can combine multiple files and show you the output of them.
In this instance the file in the directory we needed to read was called "readme".

```
ssh bandit1@localhost
```
To connect to the next level we used the SSH command again but with the bandit1 prefix as this is the next level and @localhost as we are already connected to the bandit over the wire servers.


# Level 1 → Level 2

## Level Goal
The password for the next level is stored in a file called - located in the home directory.

## Walkthrough

We are told in the level goal descriptor that the password for the next level is stored in a file called - located in the home directory. First we are again like the previous level going to confirm we are in home directory using the pwd command.

```
pwd
```
After the pwd command confirms we are in the home directory we need to list the contents of the directory to see whats there we do this using the ls command.

```
ls
```

From the ls command we can see there is a file called "-" in the home directory, so we are going to use the cat command to see the contents of this file.

```
cat ./-
```

From this command we have captured our flag for this level and obtained the password.

### Flag captured
```
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```
After capturing our flag we are going to move to the next level, which is called bandit2, using the following command.

```
ssh bandit2@localhost
```
Enter the flag from above when prompted for the password for the next level.

![bandit12-terminal-commands-screenshot](https://raw.githubusercontent.com/EoinReid/Bandit-CTF/master/Bandit-Screencaps/bandit12-1.PNG "Bandit12 Terminal Commands")

## New Commands breakdown

```
cat ./-
```
As the filename we are trying to use the cat command for is called '-' we must be careful as bash will see this '-' as a synonym for stdin or standard input to get around this we added the prefix "./" to specify the current directory to differentiate between "-" meaning stdin and a filename called "-".

# Level 2 → Level 3

## Level Goal
The password for the next level is stored in a file called spaces in this filename located in the home directory

## Walkthrough

We are told in the level goal descriptor that the password for the next level is stored in a file called spaces in this filename in the home directory.

```
pwd
```
After the pwd command confirms we are in the home directory we need to list the contents of the directory to see whats there we do this using the ls command.

```
ls
```

From the ls command we can see there is a file called spaces in this filename in the home directory, so we are going to use the cat command to see the contents of this file.

```
cat "spaces in this filename"
```

From this command we have captured our flag for this level and obtained the password.

### Flag captured
```
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```
After capturing our flag we are going to move to the next level, which is called bandit3, using the following command.

```
ssh bandit3@localhost
```
Enter the flag from above when prompted for the password for the next level.

![bandit23-terminal-commands-screenshot](https://raw.githubusercontent.com/EoinReid/Bandit-CTF/master/Bandit-Screencaps/bandit23-1.PNG "Bandit23 Terminal Commands")

## New Commands breakdown

```
cat "spaces in this filename"
```
As the filename we are trying to use the cat command for is called "spaces in this filename" if we try to use the command 

```
cat spaces in this filename
```
we will get the errors

```
cat: spaces: No such file or directory
cat: in: No such file or directory
cat:  this: No such file or directory
cat: filename: No such file or directory
```
This is due to bash reading the spaces in between each other as seperate filenames instead of the name of one file with spaces in its name, to get around this we can add "" or '' quotation marks to specify it is a file of one name with spaces in the name.

# Level 3 → Level 4

## Level Goal
The password for the next level is stored in a hidden file in the inhere directory.

## Walkthrough

```
ls
```

From the ls command we can see there is another directory called "inhere", this is the directory the level goal specified so we are going to change to that directory.

```
cd inhere
```
Changing to the inhere directory.

```
ls -a
```
As the level goal descriptor specified a "hidden" file, we are going to use the ls command in this directory with the -a attribute so that it lists all contents in this directory even hidden files.

```
cat .hidden
```
From the ls -a command we found a hidden file called .hidden, so we are going to use the cat command to print its contents to the terminal.

### Flag captured
```
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```
After capturing our flag we are going to move to the next level, which is called bandit4, using the following command.

```
ssh bandit4@localhost
```
Enter the flag from above when prompted for the password for the next level.

![bandit34-terminal-commands-screenshot](https://raw.githubusercontent.com/EoinReid/Bandit-CTF/master/Bandit-Screencaps/bandit34-1.PNG "Bandit34 Terminal Commands")

## New Commands breakdown

```
ls -a
```
Filenames that start with a "." are hidden from the directory, so using a normal ls command would turn up no results. Using the -a attritbute with the ls command allows you to see all files in a directory inlucding hidden files beginnging with "."

# Level 4 → Level 5

## Level Goal
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

## Walkthrough

```
ls
```

From the ls command we can see there is another directory called "inhere", this is the directory the level goal specified so we are going to change to that directory.

```
cd inhere
```
Changing to the inhere directory.

```
ls -l
```
As the level goal descriptor says human-readable file I used the -l attribute with the ls command to list the contents of the directory in a long format to see if it would give us some more useful information.

```
cat ./*
```
From the ls -l command we were able to learn that the files are all of the same type, so the quickest way to see the contents of all the files at once is using the cat command with ./* which will print all the contents of all the files in this directory to the terminal instead of having to cat each file manually.

### Flag captured
```
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```
After capturing our flag we are going to move to the next level, which is called bandit5, using the following command.

```
ssh bandit5@localhost
```
Enter the flag from above when prompted for the password for the next level.

![bandit45-terminal-commands-screenshot](https://raw.githubusercontent.com/EoinReid/Bandit-CTF/master/Bandit-Screencaps/bandit45-1.PNG "Bandit45 Terminal Commands")

## New Commands breakdown

```
ls -l
```
 -l for long, this shows a detailed list of files in a long format. This will show you detailed information, starting from the left: file permissions, number of links, owner name, owner group, file size, timestamp of last modification, and file/directory name. 
 
 # Level 5 → Level 6

## Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
	* human-readable
	* 1033 bytes in size
	* not executable

## Walkthrough

```
ls
```

From the ls command we can see there is another directory called "inhere", this is the directory the level goal specified so we are going to change to that directory.

```
cd inhere
```
Changing to the inhere directory.

```
ls 
```
I used the ls command to get a bearing on what is within the inhere directory this time, and from it we can see an array of different maybehere directories.

```
find -size 1033c
```
As the level goal descriptor says the file size is 1033 bytes, we can use the find command to search for a file in this directory that is 1033 bytes in size, using the -size attribute and appending c to the end of 1033 to specify to the terminal we are looking for 1033 bytes.

```
cat ./maybehere07/.file2
```
From the find command the terminal returned the file and location "./maybehere07/.file2", so I then used the cat command to print its contents to the terminal.

### Flag captured
```
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```
After capturing our flag we are going to move to the next level, which is called bandit6, using the following command.

```
ssh bandit6@localhost
```
Enter the flag from above when prompted for the password for the next level.

![bandit56-terminal-commands-screenshot](https://raw.githubusercontent.com/EoinReid/Bandit-CTF/master/Bandit-Screencaps/bandit56-1.PNG "Bandit56 Terminal Commands")

## New Commands breakdown

```
find -size 1033c
```
 The find command is heplful for finding a specific file that you don't know the location of. In the find command we used in this walkthrough we used the -size attribute to specify we are looking for a file of a particular size, in this case 1033 bytes, we then wrote the size 1033 and added a c to specify it is 1033 bytes in size.
