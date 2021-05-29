# **Linux Commands**
## **Part 1**

`echo` returns whatever is inputted into it. 

Example: 
> echo Hello World!


`man` is used to display the user manual of any command that we can run on the terminal. 
 
Example: 
> man echo


`cat` is short for concatenate, and it outputs the contents of files to the console. 

Example: 
> cat Test.txt


`touch` is used to create files.

Example: 
> touch Test.txt


`touch` is used to create files.

Example: 
> touch Test.txt


Relative Paths: Occasionally there will be times when you want to run downloaded or user created programs. This is done by providing the full path to the binary, for example say you download a binary that outputs noot, providing the full path to that binary will execute it. Every time you intend on running the binary, you don't need to provide a full path, you can use Relative Paths.

Relative Paths:
| Relative Path | Meaning | Absolute Path | Relative Path | Running a binary with a Relative Path | Running A Binary with an Absolute Path |
| ----------- | ----------- | ----------- | ----------- |----------- | ----------- |
| . | Current Directory | /tmp/aa  | . | ./hello | /tmp/aa/hello |
| .. | Directory before the current directory	 | /tmp | .. | ../hello | /tmp/hello |
| ~ | Directory before the current directory	 | /home/< current user>	 | ~ | ~/hello | /home/< user>/hello |


`su` is used to change the user, without logging out and logging back in again.

Example: 
> su root

---
## **Part 2**

`SSH` is a network protocol that enables secure remote connections between two systems. System admins use SSH utilities to manage machines, copy, or move files between systems.

Example:
> ssh user@IP

For Example:
> ssh User@10.10.10.10

### **Linux Operators**

`&&` allows you to execute a second commant after the first one has executed successfully. The first command must run properly or else the second command will not work.

Example:
> ls && echo hello


`&` is a background operator, meaning say you run a command that takes 10 seconds to run, normally you wouldn't be able to run commands during that period; however, with & that command will still execute and you'll be able to run other commands.

Example:
> sh my_script.sh &


`$` is an unusually special operator, as it is used to denote environment variables. These are variables set by the computer(You can also set thme yourself). that are used to affect different processes and how they work. Meaning that if you edit these variables you can change how certain processes work on your computer. For example your current user is always stored in an environment variable called $USER. You can view these variables with the echo command.

Example:
> echo $USER

Naturally this means environment variables can be used as input for other commands as well, for example say I wanted to create a file which is the name of our current user, I could do `touch $USER`. Environment variables can also be set pretty easily, just running `export <varname>=<value>` will set that as an environment variable


`|` is a operator called the pipe. While `>>` allows you to store the output of a command, `|` allows you to take the output of a command and use it as input for a second command. Like I can use `cat` to get the output fo a file, and pipe that into `grep` to search for a specific string.

Example:
> cat test | grep noot


`;` works a lot like &&, however it does not require the first command to execute successfully. 

Example:
> lahbsgoiang; ls


`>` is the operator for output redirection. Meaning that you can redirect the output of any command to a file. For example if I were to run `echo hello > file`, then instead of outputting hello to the console, it would save that output to a file called file. It is worth noting that if you were to use this operator on a file that already exists, it would completely erase the contents of that file and replace it with the output from your command.

Example:
> echo hello > file


`>>` does mainly the same thing as `>`, with one key difference. `>>` appends the output of a command to a file, instead of erasing it.

Example:
> echo hello >> file

### **Advance File Operators**

`chown` allows you to change the user and group for any file. The syntax for this command is chown user:group file. For example if we wanted to change the owner of file to user2 as well as the group to user2, we could use `chown user2:user2 file`.

Note: You can only use chown if you are 'above' that other user, meaning that this is best done when you are the root(administrator) user.


`chmod` allows you to set the different permissions for a file, and control who can read it. The syntax of this command is typically `chmod <permissions> <file>`. The permissions are set using a three digit number, where each digit controls a specific permission, meaning the first digit controls the permissions for a user, the second digit controls the permission for a group, the third digit controls permissions for everyone that's not a part of the user or group.

Now the value of the digits control whether they can read, write or execute it or do all three, and to properly calculate it some math needs to be done.
| Digit | Meaning |
| ----------- | ----------- |
| 1 | That file can be executed |
| 2 | That file can be written to	 |
| 3 | That file can be executed and written to |
| 4 | That file can be read |
| 5 | That file can be read and executed |
| 6 | That file can be written to and read |
| 7 | That file can be read, written to, and executed |

The way these values are calculated is this. The digit 1 means the file can be executed, the digit 2 means it can be written to, and the digit 4 means it can be read. You get the different permissions by adding these digits together. For example 1+2 is 3 meaning that file can be executed and written to. Now let's see how it all works in perspective.
| Command | Meaning |
| ----------- | ----------- |
| chmod 341 file | The file can be executed and written to by the user that owns the file. The file can be read by the group that owns the file. The file can be executed by everyone else. |
| chmod 777 file | The file can be read, written to, and executed by the user that owns the file. The file can be read, written to, and executed by the group that owns the file. The file can be read, written to, and executed by everyone else.	 |
| chmod 455 file | The file can be read by the user that owns the file. The file can be read and executed by the group that owns the file. The file can be read to and executed by everyone else. |

The File permissions are divided into three sections, user and group and everyone else. for example lets look at this `ls -al` being executed and here is one of the results: `-rw-r--r-- 1 User3 User3 807 Feb 20 01:44 .profile` Everything starts from the second hyphen not the first, so we dont even look at the first hyphen. Also note that everything is in sequential order, so the first three characters control permissions for the user, the second three characters control permissions for the group, and the final three characters control permissions for everyone else.