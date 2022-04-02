# Streams and Redirection
Every command in the terminal in linux runs on three main connections: 

>stdin: where the command gets its input

>stdout: where the normal output is printed

>sterr: all output concering errors is printed here

stdin is connected to our keyboard normally, while stdout and stderr are connected to the terminal (since the output of commands and any error is printed onto the terminal).

stdin is denoted by 0, stdout is denoted by 1 and stderr is denoted by 2

![Screenshot (439)](https://user-images.githubusercontent.com/102430622/161391221-f8740172-51f7-4278-8468-dbf111bb2bdc.png)

# Redirection

The most common forms of redircetion is the greater and less than signs. 

- source s <: denotes reading from the source s
- \> dest d: denotes writing to a destination d
- \>> dest d: denotes appending to a destination d

the command <input comm>output can be seen in the following manner in accordance to the following graph

![Screenshot (441)](https://user-images.githubusercontent.com/102430622/161391342-75ee7e80-4dd3-4fac-837e-08e529fbbdd7.png)

The following table illustrates the redirection process:

![Screenshot (443)](https://user-images.githubusercontent.com/102430622/161391547-8cdc4abf-9e70-45b7-a677-2f6603f71680.png)

# Remote Computing:

Bash can be used to access computer remotely. A computer can be accessed remotely using ssh (secure shell), scp (secure copy) and rsync commands. rsync is the most efficient out of them since it will keep retrying incase of network failure. scp and rsync work the same by providing copies of the files on the remote computer however rsync will provide a single copy of a file rather than sending duplicate files (lise scp) and it will keep retrying to copyy all files in the case of network failure.

# ftp
File Transfer Protocol: this utility helps you to connect and login to remote hosts. It allows one computer to get (download) and put (upload) files and data from and to another computer. 

$ ftp hostname or ip-address

the aboe command will prompt the user for a login and password

# Some More Commands

![Screenshot (446)](https://user-images.githubusercontent.com/102430622/161391873-03016e5c-e759-4a1a-a78c-c6af9c37bb6e.png)

# Scripting in the Shell

Variables in the shell can be Scalar (capable of holding a single value numeric or string) and array (capable of holding multiple values)

For example, we can declare varibales by simply giving a name (ex. duration=10). If a strong does not have any spaces, no need to quote them, however if it contains spaces, it needs to be quoted (ex. artist=Baauer; song="Harlem Shake").

To declare an array we can simply use the brackets (ex. cart=(apples oranges bananas))

To reference variables we need to preceed the name with a dollar symbol $ ex...

str='$song by ${artist}' --the curlies are optional; echo $str--the single quotes will not print the values of the variables but rather print the word "$song" (they do not interpolate)

str="$song by $artist" will print the values of the variables

echo ${cart[0]} --here the curly brackets are required, this displays the first element in the array (apple)

To print the whole array we can use echo ${cart[\*]} or echo ${cart[@]}

-> print string length: echo ${#str}

- substring: ${str:7}--prints from char 8 till the end. ${str:7:8} will print starting from char 8 and only 8 characters. so $str="hello my name is kamil". echo ${str:7:8} will print "y name i" (y is the 8th character and the total length of the substring is 8 characters)

- echo ${str: -6} will only print the last 6 characters. the space before the -6 is necessory for it to work

- echo ${str#?} will print everything except the first character

- echo ${str%?} will print everything except the last character

- to find and replace just use echo ${str//Harlem//UMBC}--this will find Harlem and replace it with UMBC

- It should be noted that environment variables (reserved variables such as $PATH and $HOME) are always in all caps while local script variables tend to be in lowercase. vairiable naming is case sensitive

If a script file let's say called args.sh takes arguments I can echo those arguments. For examgple $./args.sh foo bar... I can echo the name of the file by echo $0; echo the number of arguments by echo $# (2); echo the arguments using echo $1 for the 1st argument ($n for the nth argument). If I have more than 10 arguments I use the curly bracelets (echo ${11}--will echo the 11th argument). to print all the arguments just do echo $*

# Some Special Variables

- $$ will print the pid of the current process 
- $PPID will the PID of the Parent Process of the current process
- $? will print the exit status of the process. If the exit status is 0 then the process terminated without successfully. If it is greater than 0 then it terminated unsuccessfully

# Globbing

Globbing is similar to REGEX. 

- A question mark ? will denote a single character in this position. so ls ?.txt will print all txt files that have names of a single character

- \* 0 or more occurences. so ls \*.txt will match all files with the txt extension

- [-] will match anything in the character class  

- {---,---,---} will match anything (atleast 1) in this set.
- We can combine the globbing like ls \*{.txt,.sh} to print all files that are either txt files or shell files

