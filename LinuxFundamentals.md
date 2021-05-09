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